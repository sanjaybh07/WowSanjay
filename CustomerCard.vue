<template>
  <v-card class="mx-auto" elevation="10">
      <div class="pa-2 d-flex justify-space-between align-center">
        <v-icon>mdi-minus-circle-outline</v-icon>
        <v-btn class="px-5" rounded="xl">Valid</v-btn>
      </div>
  </v-card>
  <v-row>
    <v-col v-for="n in 6" :key="n" cols="4">
      
      <v-sheet
        rounded="xl"
        elevation="2"
        border="lg"
        max-width="450"
        class="mt-10" 
      >
      <v-container>
        <div class="d-flex mr-2 justify-end">
          <v-switch hide-details color="purple">
            <template v-slot:prepend>
              <span class="text-caption text-blue">Active</span>
            </template>
          </v-switch>
        </div>
        <div class="text-center" style="margin-top: -110px">
          <v-avatar size="90" image="@/assets/john.jpg"></v-avatar>
          <p class="text-h6 font-weight-bold" style="color: #0010a4">
            John Becket
          </p>
          <p class="text-h6 font-weight-bold">987456</p>
        </div>

        <v-container>
          <div class="d-flex justify-space-between align-center">
            <div class="d-flex flex-column align-center">
              <v-card width="25">
                <v-img height="30" src="@/assets/john.jpg" cover></v-img>
              </v-card>
              <span class="text-caption">Manager</span>
              <span class="text-caption font-weight-bold">Arvind - 112244</span>
            </div>

            <div class="d-flex flex-column align-center">
              <v-icon
                size="25"
                icon="mdi-file-percent"
                class="text-primary"
              ></v-icon>
              <span class="text-caption">Discount</span>
              <span class="text-caption font-weight-bold">30%</span>
            </div>

            <div class="d-flex flex-column align-center">
              <v-icon size="25" icon="mdi-calendar-month text-primary"></v-icon>
              <span class="text-caption">Year</span>
              <span class="text-caption font-weight-bold">2022-23</span>
            </div>

            <div class="d-flex flex-column align-center">
              <v-icon size="25" icon="mdi-tag text-primary"></v-icon>
              <span class="text-caption">Discount Limit</span>
              <span class="text-caption font-weight-bold">30,000</span>
            </div>
          </div>
          <v-sheet border="sm" class="pa-2 my-2" rounded="lg">
            <div class="d-flex flex-column align-left">
              <span class="text-caption font-weight-bold">Remarks:</span>
              <span class="text-medium-emphasis text-caption font-weight-light"
                >Lorem ipsum dolor sit amet consectetur adipisicing elit.
                Repellendus vero rem reprehenderit sunt ut optio error aliquam
                exercitationem consequuntur sit ipsa repudiandae, dignissimos
                fuga a dolorem, vel dicta natus voluptates!</span
              >
            </div>
          </v-sheet>
        </v-container>
      </v-container>
      </v-sheet>
    
    </v-col>
  </v-row>
</template>

<style scoped>
.percent-box {
  transform: rotate(-45deg);
}
.cardPosition {
  position: relative;
  overflow: visible;
}

.avatarContainer {
  position: absolute;
  top: -50%;
  left: -50%;
}
</style>
