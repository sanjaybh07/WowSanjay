<template>
  <v-card
    rounded="xl"
    max-width="550"
    theme="dark"
    style="background-color: #5c7288"
  >
    <v-container>
      <div class="d-flex align-center">
        <span>22-Feb-2024 , 12:00 AM-</span>
        <v-spacer></v-spacer>
        <v-switch inset hide-details density="compact" v-model="switchVal">
          <template v-slot:prepend>
            <span class="ms-15">Valid</span>
          </template>
        </v-switch>
      </div>

      <div class="d-flex align-center justify-space-between">
        <div class="d-flex flex-column">
          <span class="font-weight-black text-h5">01O0000289</span>
          <span
            >Type -
            <span style="color: #00ffc2" class="font-weight-bold"
              >Inventory</span
            >
          </span>
        </div>
        <v-sheet
          rounded="xl"
          style="background-color: #e7f1fa"
          class="px-2 py-1"
        >
          <span class="text-body-2 text-grey-darken-1">GRN -</span>
          <span class="ms-1 text-black text-subtitle-2">Not Created</span>
          <v-icon
            icon="mdi-circle"
            class="text-caption ms-1"
            color="red"
          ></v-icon>
        </v-sheet>
      </div>

      <v-sheet
        style="background-color: #ffffff"
        rounded="lg"
        class="my-2 px-4 py-6 d-flex align-center justify-space-between"
      >
        <span class="text-blue-darken-2 font-weight-bold">Party</span>
        <span class="text-black font-weight-bold text-body-1"
          >03-WAREHOUSE SOR</span
        >
        <span class="text-black">Ref.no - </span>
      </v-sheet>
      <v-sheet
        style="background-color: #ffffff"
        rounded="lg"
        class="my-2 px-4 py-6 d-flex align-center justify-space-between"
      >
        <span class="text-blue-darken-2 font-weight-bold">Transporter</span>
        <span class="text-black font-weight-bold text-body-1"
          >ABC TRANSPORT</span
        >
        <span class="text-black">Builty.no - 00001</span>
      </v-sheet>

      <div class="d-flex align-center justify-space-between">
        <div class="d-flex justify-space-between w-50">
          <div>
            <span>Boxes</span>
            <span>1</span>
          </div>
          <div>
            <span>Qty</span>
            <span>3</span>
          </div>
          <div>
            <span>Weight</span>
            <span>0</span>
            <span>KG</span>
          </div>
        </div>

        <div>
          <span>0</span>
          <v-icon>mdi-paperclip</v-icon>
        </div>
      </div>
    </v-container>
  </v-card>
</template>

<script>
export default {
  data() {
    return { switchVal: true };
  },
};
</script>

<style scoped>
.custom-thumb {
  background-color: #1976d2; /* Custom background color */
  border-radius: 50%; /* Rounded corners */
  padding: 4px; /* Add some padding */
}
</style>
