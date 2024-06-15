<template>
  <!-- <v-sheet min-width="100vw" style="background-color: #000042" theme="dark"> -->
  <v-card
    flat
    style="background-color: #000042"
    min-width="100vw"
    min-height="100vh"
    theme="dark"
    class="d-flex align-center"
  >
    <v-card
      rounded="xl"
      :class="imgClass"
      theme="dark"
      variant="outlined"
      style="border-color: blue"
      min-height="60vh"
    >
      <div class="d-flex flex-column align-center justify-end" :style="imgDivStyle">
        <!-- <v-img v-if="!showOrgImage" src="@/assets/wizapp.svg" inline :width=imgWidth> </v-img> -->
          <v-img src="@/assets/wizapp.svg" style="width: 1000px !important">
          </v-img>
        <span class="text-h4 font-weight-black">Wizapp-on-Web</span>
      </div>

      <div :style="inputDivStyle" :class="inputDivClass">
        <v-select
          variant="underlined"
          label="Saved login detail"
          hide-details
          density="compact"
        >
          <template v-slot:prepend>
            <v-icon color="primary">mdi-account-clock-outline</v-icon>
          </template>
        </v-select>
        <v-text-field
          variant="underlined"
          label="E-mail"
          placeholder="Type your company E-mail"
          density="compact"
          :rules="[rules.required,rules.email]"
        >
          <template v-slot:prepend>
            <v-icon color="primary">mdi-email</v-icon>
          </template>
          <template v-slot:append>
            <v-btn icon plain> <v-icon color="primary">mdi-arrow-right</v-icon></v-btn>
          </template>

        </v-text-field>
        <v-select
          variant="underlined"
          label="Username"
          hide-details
          density="compact"
          :rules="[rules.required]"
        >
          <template v-slot:prepend>
            <v-icon color="primary">mdi-account</v-icon>
          </template>
        </v-select>
        <v-text-field
          variant="underlined"
          label="Enter password"
          :type="showPassword ? 'password' : 'text'"
          :error-messages="password.errorMessage.value"
          density="compact"
          v-model="password.value.value"
        >
          <template v-slot:prepend>
            <v-icon color="primary">mdi-key-variant</v-icon>
          </template>
          <template v-slot:append-inner>
            <v-btn
              @click="showPassword = !showPassword"
              class="ma-0"
              variant="text"
              size="small"
            >
              <v-icon end size="x-large" color="primary">{{
                showPassword ? "mdi-eye-off-outline" : "mdi-eye-outline"
              }}</v-icon>
            </v-btn>
          </template>
        </v-text-field>
        <v-select
          variant="underlined"
          label="Enter location"
          hide-details
          density="compact"
          v-model="location.value.value"
          :error-messages="location.errorMessage.value"
        >
          <template v-slot:prepend>
            <v-icon color="primary">mdi-map-marker</v-icon>
          </template>
        </v-select>
        <v-btn rounded="xl" size="x-large" class="text-white bg-blue-lighten-2"
          >Login</v-btn
        >
      </div>
    </v-card>
  </v-card>
</template>

<script setup>
import { onMounted, ref, computed } from "vue";
import {useForm,useField} from "vee-validate"


const email=useField("email")
const userName=useField("user")
const password=useField("password")
const location=useField("location")

const showOrgImage = ref(false);

const showPassword = ref(true);
const screensize = ref("large");
const screenWidth = ref(window.innerWidth);


const {handleSubmit,handleReset} = useForm({
  validationSchema : {
    email(value) {
      if (!value || value=="") return "Email required"

      const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      return pattern.test(value) || 'Invalid email'

    },

    userName(value) {
      if (!value || value=="") return "Username can't be left blank"

      return true

    },

    password(value) {
      if (!value || value=="") return "Password can't be empty"

      return true
    },

    location(value) {
      if (!value || value!="") return "Please choose a valid location"

      return true
    }
  }
})

const imgWidth = computed(() => {
  return imgRatio.value * window.innerWidth;
});

const rules =ref({
  required : (val)=>(val && val!="") || 'field required',
  email : (val)=> {
    const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
    return pattern.test(val) || 'Invalid email'
  }
})


const inputDivStyle = computed(() => {
  if (showOrgImage.value) return "height: 500px";
  else return "width: 60%";
});

const inputDivClass = computed(() => {
  if (showOrgImage.value)
    return "d-flex flex-column ma-10 justify-space-between";
  else return "d-flex flex-column  ma-10";
});

const imgDivStyle = computed(() => {
  if (showOrgImage.value) return "width:100%; margin-top: -50px;";
  else return "width:40%;margin-top: -50px;";
});

const imgClass = computed(() => {
  let retClass = "";

  if (screensize.value == "large") {
    retClass = "bg-transparent mx-auto my-auto d-flex";
  } else {
    retClass = "bg-transparent mx-auto d-flex flex-column";
  }

  return retClass;
});

const imgRatio = ref();
onMounted(() => {
  window.addEventListener("resize", checkScreenSize);
  imgRatio.value = 350 / window.innerWidth;
});

const checkScreenSize = () => {
  screensize.value = window.innerWidth < 960 ? "small" : "large";

  showOrgImage.value = window.innerWidth < 960 ? true : false;

  console.log("showOrgImage", showOrgImage.value);
  console.log("Class of img", imgClass.value);
  console.log("Style of imgDiv", imgDivStyle.value);
};
</script>
