<template>
  <div v-if="mainTab == '1'" class="text-center">
    <v-overlay class="custom-overlay" absolute opacity="0" />

    <v-dialog
      v-model="custSearchOn"
      class="customDialog"
      width="500"
      transition="slide-x-transition"
      background="rgba(33, 33, 33, 0.50)"
    >
      <v-card width="500" height="100vh">
        <v-container>
          <div
            class="d-flex font-weight-bold align-center justify-space-between"
          >
            <span>Search results for</span>

            <v-btn variant="text" @click="custSearchOn = false"
              ><v-icon class="ps-7" size="26"  end
                >mdi-close</v-icon
              ></v-btn
            >
          </div>
          <div class="d-flex justify-space-between align-center">
            <v-btn
              rounded="xl"
              class="text-caption"
              theme="dark"
              style="background-color: #3e4758;"
            >
              <v-icon start>mdi-plus</v-icon> Add New Cust</v-btn
            >
            <v-card width="300">
              <v-text-field
              
                clearable
                prepend-inner-icon="mdi-magnify"
                variant="outlined"
                hide-details
                density="compact"
              >
              </v-text-field>
            </v-card>
          </div>

          <span class="text-caption">
            You can search for customers list by typing their mobile number /
            customer ID / first name / last name / Email / GST no etc.
          </span>
        </v-container>
      </v-card>
    </v-dialog>
  </div>

  <v-sheet class="d-flex justify-space-between">
    <div class="d-flex align-center">
      <v-icon>mdi-arrow-left</v-icon>
      <span class="ms-2 text-h6">Adding new Bill</span>
    </div>
    <div v-if="mainTab == 1">
      <v-btn
        class="text-none text-grey"
        rounded="xl"
        width="80"
        variant="outlined"
        >Cancel</v-btn
      >
      <v-btn class="ms-4 text-none bg-primary" width="80" rounded="xl"
        >Next</v-btn
      >
    </div>
    <v-card flat width="450" v-else class="d-flex justify-space-between">
      <v-btn-toggle
        v-model="cmm.pay_mode"
        density="compact"
        rounded="xl"
        variant="outlined"
        selected-class="colorPaymode"
      >
        <v-btn>
          <v-icon>mdi-currency-inr</v-icon>
        </v-btn>
        <v-btn> CC </v-btn>
        <v-btn>
          <v-icon>mdi-credit-card-outline</v-icon>
        </v-btn>
      </v-btn-toggle>
      <v-btn
        rounded="xl"
        class="text-none text-white text-caption"
        style="background-color: #121212"
        >Save & Print</v-btn
      >
      <v-btn class="text-none bg-primary text-caption" rounded="xl">Save</v-btn>
    </v-card>
  </v-sheet>
  <v-sheet class="d-flex">
    <div
      style="width: 700px"
      v-if="cmm.customer_code"
      class="d-flex justify-space-between"
    >
      <div>
        <span class="me-2">Customer</span>
        <span class="text-primary font-weight-bold"
          >{{ cmm.customer_code }} | {{ cmm.customer_name }}
        </span>
      </div>
      <div>
        <v-icon @click="" color="#555F71" size="large">mdi-pencil-box</v-icon>
        <v-icon @click="" color="#555F71" size="large"
          >mdi-arrow-right-box</v-icon
        >
      </div>
    </div>
    <v-card
      v-if="mainTab == '2'"
      class="d-flex align-center justify-space-between"
      max-width="900"
      flat
    >
      <div>
        <span class="mr-4">Sold Qty & Amt</span>
        <span style="color: #2a8835" class="font-weight-bold"
          >5 | <v-icon size="small">mdi-currency-inr</v-icon>9696</span
        >
      </div>

      <div>
        <span class="mr-2">Return Qty & Amt</span>
        <span style="color: #de3730" class="font-weight-bold"
          >00 | <v-icon size="small">mdi-currency-inr</v-icon>00.00</span
        >
      </div>

      <div style="color: #005eb4" class="text-h6 font-weight-bold">
        <span class="mr-4">Net Amt</span>
        <span class="text-primary font-weight-bold"
          ><v-icon size="small">mdi-currency-inr</v-icon>9696</span
        >
        <v-icon @click="" size="xx-large" style="color: #555f71"
          >mdi-arrow-right-box</v-icon
        >
      </div>
    </v-card>
  </v-sheet>

  <v-card>
    <v-tabs v-model="mainTab">
      <v-tab value="1" color="primary"> Bill View </v-tab>
      <v-tab value="2" color="primary"> Product List </v-tab>
      <v-tab value="3" color="primary"> Payment </v-tab>
    </v-tabs>
  </v-card>
  <v-window v-model="mainTab">
    <v-window-item value="1">
      <v-card class="d-flex mt-2" width="300" flat>
        <v-spacer></v-spacer>
        <a
          @click.prevent="custSearchOn = true"
          target="none"
          href="none"
          class="text-h6 text-black"
          style="cursor: default !important"
          >Search for Customer</a
        >
      </v-card>

      <v-card max-width="1000" flat>
        <p>Add Sales Person</p>
        <div class="mt-4 d-flex justify-space-between">
          <div>
            <v-autocomplete
              label="Sales Person1"
              variant="outlined"
              :items="spLov"
              item-title="emp_name"
              item-value="emp_code"
              v-model="cmm.sp1"
              style="width: 300px"
              clearable
            ></v-autocomplete>
          </div>
          <div>
            <v-autocomplete
              label="Sales Person2"
              :items="spLov"
              item-title="emp_name"
              item-value="emp_code"
              v-model="cmm.sp2"
              variant="outlined"
              style="width: 300px"
              clearable
              clear-icon="mdi-close"
            ></v-autocomplete>
          </div>
          <div>
            <v-autocomplete
              label="Sales Person3"
              :items="spLov"
              item-title="emp_name"
              item-value="emp_code"
              v-model="cmm.sp3"
              variant="outlined"
              style="width: 300px"
              clearable
            ></v-autocomplete>
          </div>
        </div>
        <v-divider></v-divider>
        <div class="d-flex mt-2">
          <v-row>
            <v-col cols="3">
              <span>Remarks</span>
            </v-col>
            <v-col>
              <v-textarea
                rows="3"
                rounded="lg"
                variant="outlined"
                clearable
                clear-icon="mdi-close"
              >
                <template v-slot:clear-icon>
                  <v-icon>mdi-account</v-icon>
                </template>
              </v-textarea>
            </v-col>
          </v-row>
        </div>
      </v-card>
    </v-window-item>

    <v-window-item value="3" title="Payment entry">
      <v-container class="my-2">
        <div>
          <span>Net Amount</span>
          <span><v-icon>mdi-currency-inr</v-icon></span>
          <span>{{ cmm.net_amount }}</span>
        </div>
        <v-card
          flat
          width="500"
          class="d-flex align-center justify-space-between"
        >
          <div>
            <span>Total payment</span>
            <span><v-icon>mdi-currency-inr</v-icon></span>
            <span>{{ totalPayment }}</span>
          </div>
          <div>
            <span class="text-subtitle-2 me-2">Balance</span>
            <span class="text-red-darken-4 font-weight-black"
              ><v-icon size="x-small" end>mdi-currency-inr</v-icon>
              {{ balanceAmt }}</span
            >
          </div>
        </v-card>
      </v-container>
      <v-row>
        <v-col v-for="(payment, index) in payments" :key="index">
          <v-card elevation="5" max-width="500">
            <v-container>
              <v-row class="align-bottom">
                <v-col cols="4">
                  <span>Payment Mode</span>
                  <v-select
                    variant="underlined"
                    hide-details
                    v-model="payment.paymode"
                    :items="payModesLov"
                    item-title="payModeName"
                    item-value="paymodeCode"
                  >
                  </v-select>
                </v-col>
                <v-col cols="4">
                  <p>Amt</p>
                  <v-text-field
                    class="text-primary"
                    v-model="payment.amount"
                    hide-details
                    variant="underlined"
                    clearable
                    
                  >
                    <template v-slot:prepend-inner>
                      <v-icon>mdi-currency-inr</v-icon>
                    </template>
                  </v-text-field>
                </v-col>
                <v-col cols="4">
                  <span
                    >Reference No
                    <v-icon size="small" @click="delPayment(index)"
                      >mdi-trash-can-outline</v-icon
                    ></span
                  >
                  <v-text-field
                    hide-details
                    variant="underlined"
                    density="compact"
                    v-model="payment.refNo"
                    clearable
                  >
                  </v-text-field>
                </v-col>
              </v-row>
              <v-row>
                <v-col>
                  <v-textarea
                    placeholder="Remarks"
                    hide-details
                    variant="outlined"
                    rows="1"
                    auto-grow
                  ></v-textarea>
                </v-col>
              </v-row>
            </v-container>
          </v-card>
        </v-col>
      </v-row>
      <div class="text-center">
        <v-btn
          @click="addPayment"
          rounded="xl"
          class="text-none"
          color="primary"
          ><v-icon>mdi-plus</v-icon> Add New</v-btn
        >
      </div>
    </v-window-item>
    <v-window-item value="2">
      <v-card
        max-width="450"
        flat
        class="mt-5"
      >
        <v-row>
          <v-col cols="7">
            <v-btn-toggle
              v-model="scanMode"
              divided
              border
              rounded="lg"
              
              style="height: 50px"
            >
              <!-- #003062 -->
              <v-btn color="#003062" size="small"
                ><v-icon size="x-large">mdi-camera-plus-outline</v-icon></v-btn
              >
              <v-btn color="#003062" size="small"
                ><v-icon size="x-large">mdi-form-dropdown</v-icon></v-btn
              >
              <v-btn color="#003062" size="small"
                ><v-icon size="x-large">mdi-barcode-scan</v-icon></v-btn
              >
            </v-btn-toggle>
          </v-col>
          <v-col cols="5">
            <div class="d-flex align-center justify-space-around">
              <span :class="!slrMode ? 'font-weight-bold' : null">Sold</span>
              <v-switch v-model="slrMode" hide-details></v-switch>
              <span :class="slrMode ? 'font-weight-bold' : null">Return</span>
              <v-btn flat size="medium" class="">
                <v-icon class="text-medium-emphasis">mdi-magnify</v-icon></v-btn
              >
            </div>
          </v-col>
        </v-row>
      </v-card>

      <v-card max-width="200" flat>
        <v-text-field
          placeholder="Type Product Code"
          variant="underlined"
          size="x-large"
          color="blue"
          clearable
        >
        </v-text-field>
      </v-card>

      <div class="d-flex">
        <v-row>
          <v-col
            v-for="(item, index) in items"
            :key="index"
            cols="12"
            sm="6"
            md="6"
            lg="4"
            xl="3"
          >
            <v-card
              elevation="5"
              width="450"
              height="250"
              rounded="lg"
              class="ms-15"
            >
              <v-container>
                <div class="d-flex">
                  <div style="height: 10px">
                    <v-avatar size="100" rounded="lg">
                      <v-img src="@/assets/jutti.png" cover></v-img>
                    </v-avatar>
                  </div>
                  <div class="ms-4 w-100" style="height: 100px">
                    <v-row style="height: 45px">
                      <v-col cols="9">
                        <div class="d-flex flex-column">
                          <span
                            style="color: #000042"
                            class="font-weight-black text-subtitle-2"
                            >{{ item.itemCode }}</span
                          >
                          <span
                            class="text-caption text-grey-darken-1 font-weight-black"
                            >{{ item.sectionName }} /
                            {{ item.subSectionname }}</span
                          >
                        </div>
                      </v-col>
                      <v-col cols="3">
                        <v-btn flat
                          ><v-icon @click="deleteItem(index)"
                            >mdi-trash-can-outline</v-icon
                          ></v-btn
                        >
                      </v-col>
                    </v-row>

                    <v-row style="height: 35px">
                      <v-col>
                        <div class="d-flex justify-space-between">
                          <div class="text-caption">
                            <span>Qty | </span
                            ><span
                              :class="
                                `${
                                  item.quantity > 0
                                    ? 'text-red'
                                    : 'text-primary'
                                }` + ' font-weight-black'
                              "
                            >
                              <v-icon size="xx-small"
                                >{{
                                  item.quantity > 0 ? "mdi-plus" : "mdi-minus"
                                }} </v-icon
                              >{{ item.quantity }}</span
                            >
                          </div>
                          <div class="text-subtitle-2">
                            <span>Bin Name </span>
                            <span class="text-primary">
                              {{ item.rackName }}</span
                            >
                          </div>
                        </div>
                      </v-col>
                    </v-row>

                    <v-row style="height: 20px">
                      <v-col>
                        <div class="text-body-2 d-flex justify-space-between">
                          <div>
                            <span class="text-subtitle-2"
                              >MRP
                              <v-icon color="primary" size="x-small"
                                >mdi-currency-inr</v-icon
                              ></span
                            >
                            <span class="text-primary font-weight-bold">{{
                              item.mrp
                            }}</span>
                          </div>
                          <div>
                            <span class="text-subtitle-2"
                              >Net Amt
                              <v-icon color="primary" size="x-small"
                                >mdi-currency-inr</v-icon
                              ></span
                            >
                            <span class="text-primary font-weight-bold">{{
                              item.itemNet
                            }}</span>
                          </div>
                        </div>
                      </v-col>
                    </v-row>
                  </div>
                </div>

                <v-tabs
                  v-model="item.tab"
                  hide-slider
                  :show-arrows="false"
                  selected-class="selectedItem"
                >
                  <v-tab
                    :ripple="false"
                    value="1"
                    style="width: 0; margin: 0px"
                  >
                    <v-chip variant="outlined" class="text-caption"
                      >Discount</v-chip
                    >
                  </v-tab>
                  <v-tab
                    :ripple="false"
                    value="2"
                    style="width: 0; margin-left: -10px"
                    
                  >
                    <v-chip variant="outlined" class="text-caption">GST</v-chip>
                  </v-tab>
                  <v-tab
                    :ripple="false"
                    value="3"
                    style="width: 0; margin: 0px"
                  >
                    <v-chip variant="outlined" class="text-caption"
                      >Sales Person</v-chip
                    >
                  </v-tab>
                  <v-tab
                    :ripple="false"
                    value="4"
                    style="width: 0; margin: 0px"
                  >
                    <v-chip variant="outlined" class="text-caption"
                      >Others</v-chip
                    >
                  </v-tab>
                </v-tabs>

                <v-window v-model="item.tab">
                  <v-window-item value="1">
                    <v-container class="text-caption">
                      <p>Scheme</p>
                      <v-row>
                        <v-col cols="4">
                          <p>Amount</p>
                        </v-col>
                        <v-col cols="8">
                          <span class="font-weight-bold"
                            >0% /
                            <v-icon size="small">mdi-currency-inr</v-icon>
                            0</span
                          >
                        </v-col>
                      </v-row>
                    </v-container>
                  </v-window-item>

                  <v-window-item value="2">
                    <div class="text-caption d-flex justify-space-between">
                      <span style="width: 55px">HSN Code</span>
                      <span style="width: 50px">GST%</span>
                      <span style="width: 30px">GST Type</span>
                      <span style="width: 30px">GST Amt</span>
                      <span style="width: 60px">GST Cess %</span>
                      <span style="width: 80px">GST Cess Amt</span>
                    </div>
                  </v-window-item>

                  <v-window-item value="3">
                    <div class="d-flex font-weight-bold" style="color: #121212">
                      <span class="mr-4" v-if="cmm.sp1 != ''">{{
                        cmm.sp1
                      }}</span>
                      <span class="mr-4" v-if="cmm.sp2 != ''">{{
                        cmm.sp2
                      }}</span>
                      <span class="mr-4" v-if="cmm.sp3 != ''">{{
                        cmm.sp3
                      }}</span>
                    </div>
                  </v-window-item>

                  <v-window-item value="4">
                    <v-row class="text-caption">
                      <v-col cols="6">
                        <div class="d-flex justify-space-between">
                          <p>Buyer Order No</p>
                          <p class="font-weight-black">{{ cmm.order_no }}</p>
                        </div>
                      </v-col>
                      <v-col cols="6">
                        <div class="d-flex justify-space-between">
                          <p>Alteration</p>
                          <p class="font-weight-black">
                            {{ cmm.alteration ? "Yes" : "No" }}
                          </p>
                        </div>
                      </v-col>
                    </v-row>
                    <v-row class="text-caption">
                      <v-col cols="6">
                        <div class="d-flex justify-space-between">
                          <p>Pack Slip No</p>
                          <p class="font-weight-black">{{ cmm.order_no }}</p>
                        </div>
                      </v-col>
                      <v-col cols="6">
                        <div class="d-flex justify-space-between">
                          <p>Alteration Type</p>
                          <p class="font-weight-black">
                            {{ cmm.alterationType }}
                          </p>
                        </div>
                      </v-col>
                    </v-row>
                  </v-window-item>
                </v-window>
              </v-container>
            </v-card>
          </v-col>
        </v-row>
      </div>
    </v-window-item>
  </v-window>
</template>

<script>
export default {
  data() {
    return {
      custSearchOn: false,
      spLov: [
        { emp_code: "01", emp_name: "rohit" },
        { emp_code: "02", emp_name: "ramesh" },
        { emp_code: "03", emp_name: "satish" },
        { emp_code: "04", emp_name: "Rahat" },
      ],

      payments: [],
      payModesLov: [
        { payModeCode: "0000000", payModeName: "INR" },
        { payModeCode: "0000002", payModeName: "HDFC CARD" },
        { payModeCode: "0000003", payModeName: "Credit Notes" },
        { payModeCode: "0000004", payModeName: "Advances" },
      ],
      cmm: {
        customer_code: "9811207344",
        customer_name: "Sanjiv Sir BHATIA",
        order_no: "AB-3456",
        alterationType: "",
        alteration: false,
        sp1: "rohit",
        sp2: "ramesh",
        sp3: "satish",
        pay_mode: 0,
        net_amount: 4398.0,
      },
      items: [
        {
          itemCode: "0121281",
          sectionName: "MENS",
          subSectionname: "Jeans",
          quantity: 1,
          rackName: "DEFAULT BIN",
          mrp: 2199,
          itemNet: 2199,
          imageName: "D:StudyVueJS\vuetify\vuetifyProjsrcassetsjutti.png",
          tab: 1,
        },
        {
          itemCode: "0121280",
          sectionName: "MENS",
          subSectionname: "Jeans",
          quantity: -1,
          rackName: "DEFAULT BIN",
          mrp: 2199,
          itemNet: 2199,
          imageName: "D:StudyVueJS\vuetify\vuetifyProjsrcassetsjutti.png",
          tab: 1,
        },
        {
          itemCode: "01212812",
          sectionName: "MENS",
          subSectionname: "Jeans",
          quantity: -1,
          rackName: "DEFAULT BIN",
          mrp: 2199,
          itemNet: 2199,
          imageName: "D:StudyVueJS\vuetify\vuetifyProjsrcassetsjutti.png",
          tab: 1,
        },
        {
          itemCode: "01212802",
          sectionName: "MENS",
          subSectionname: "Jeans",
          quantity: -1,
          rackName: "DEFAULT BIN",
          mrp: 2199,
          itemNet: 2199,
          imageName: "D:StudyVueJS\vuetify\vuetifyProjsrcassetsjutti.png",
          tab: 1,
        },
        {
          itemCode: "01212805",
          sectionName: "MENS",
          subSectionname: "Jeans",
          quantity: -1,
          rackName: "DEFAULT BIN",
          mrp: 2199,
          itemNet: 2199,
          imageName: "D:StudyVueJS\vuetify\vuetifyProjsrcassetsjutti.png",
          tab: 1,
        },
      ],
      mainTab: null,
      scanMode: 1,
      slrMode: false,
    };
  },
  computed: {
    
    totalPayment() {
     return this.payments.reduce((total,payment)=>total+payment.amount,0)
    },

    balanceAmt() {
    return this.cmm.net_amount - this.totalPayment
    }
  },
  methods: {
    deleteItem(itemIndex) {
      this.items.splice(itemIndex, 1);
    },
    addPayment() {
      const paymentItem = {
        paymode: "",
        amount: 0,
        refNo: "",
        remarks: "",
      };

      console.log("Net Amount:", this.cmm.net_amount);
     console.log("Total Payment:", this.totalPayment);
      console.log("Balance Amount:", Math.max(0, this.cmm.net_amount - this.totalPayment));
      this.payments.push(paymentItem);
    },

    delPayment(index) {
      this.payments.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.selectedItem .v-chip {
  background-color: #000042;
  color: white;
}

.colorPaymode {
  background-color: #d89b00;
  color: white;
}

.v-tabs__wrapper {
  overflow-x: hidden;
}

.customDialog {
  position: absolute;
  margin: 0;
  right: 0;
}

.custom-overlay {
  background-color: rgba(255, 0, 0, 0.5); /* Change the color as needed */
}
</style>
