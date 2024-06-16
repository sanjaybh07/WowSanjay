<template>
  <div class="mx-5 d-flex justify-space-between align-center">
    <span>9U - OCTAVE APPARELS</span>
    <v-card class="d-flex justify-space-between" width="900" flat>
      <div>
        <v-avatar size="x-small" color="#ECF1FF"></v-avatar>
        <span class="ms-1">Sale</span>
      </div>
      <div>
        <v-avatar size="x-small" color="#D6E3FF"></v-avatar>
        <span class="ms-1">Stock</span>
      </div>
      <div>
        <v-avatar size="x-small" color="#A8C8FF"></v-avatar>
        <span class="ms-1">Sell thru%</span>
      </div>
      <div>
        <v-avatar size="x-large" color="#77ACFF"></v-avatar>
        <span class="ms-1">DOS</span>
      </div>
      <div>
        <v-avatar size="x-small" color="#FFEBFF"></v-avatar>
        <span class="ms-1">GIT Qty</span>
      </div>
      <div>
        <v-avatar size="x-small" color="#F8D8FE"></v-avatar>
        <span class="ms-1">OOH Qty</span>
      </div>
      <div>
        <v-avatar size="x-small" color="#D9E3F8"></v-avatar>
        <span class="ms-1">Sugested Refill Qty</span>
      </div>
      <div>
        <v-avatar size="x-small" color="#ECF1FF"></v-avatar>
        <span class="ms-1">User Refill Qty</span>
      </div>
    </v-card>

    <div class="d-flex align-center justify-space-between" style="width: 21%">
      <v-switch inset hide-details label="Show Image"></v-switch>
      <v-btn rounded="xl" variant="outlined" class="text-none">Cancel</v-btn>
      <v-btn rounded="xl" class="bg-primary text-none">Submit</v-btn>
    </div>
  </div>

  <DataTable :value="items" tableStyle="min-width: 50rem">
    <ColumnGroup type="header" class="custom-column-group">
      <Row>
        <Column header="Image" style="background-color: #ecf1ff"></Column>
        <Column header="Article No." style="background-color: #ecf1ff" />
        <Column header="Color" style="background-color: #ecf1ff" />
      </Row>
      <Row>
        <Column :colspan="8" style="background-color: #ecf1ff; width: 20%">
          <template #header>
            <div class="w-100 d-flex justify-center">
              <span>Details</span>
            </div>
          </template>
        </Column>
        <Column style="width: 60%">
          <template #header>
            <div
              class="w-100 d-flex justify-center"
              style="background-color: #d6e3ff"
            >
              <span>Size</span>
            </div>
          </template>
        </Column>
      </Row>
    </ColumnGroup>
    <Column></Column>
    <Column field="articleNo"></Column>
    <Column field="colour"></Column>
    <Column
      header="SLS"
      field="slsQty"
      style="background-color: #f0f0f0; color: black"
    />
    <Column
      header="STK"
      field="stockQty"
      style="background-color: #f0f0f0; color: black"
    />
    <Column
      header="ST%"
      field="sellThru"
      style="background-color: #f0f0f0; color: black"
    />
    <Column
      header="DOS"
      field="daysOfStock"
      style="background-color: #f0f0f0; color: black"
    />
    <Column
      header="SRQ"
      field="suggestedRefillQty"
      style="background-color: #f0f0f0; color: black"
    />
    <Column
      header="MS%"
      field="maxStockPct"
      style="background-color: #f0f0f0; color: black"
    />
    <Column
      header="PLQ"
      field="plannedQty"
      style="background-color: #f0f0f0; color: black"
    />
    <Column
      header="MSL"
      field="maxStockLevel"
      style="background-color: #f0f0f0; color: black"
    />

    <template #footer>
      In total there are {{ items ? items.length : 0 }} products.
    </template>
  </DataTable>
</template>

<!-- :header-props=""-- {style: {backgroundColor: '#ECF1FF'}} -->

<script>
export default {
  data() {
    return {
      rowStyle: { fontStyle: "italic" },

      items: [
        {
          sectionName: "MEN",
          subSectionName: "KURTA H/S",
          articleNo: "M-110-24",
          colour: "GREY",
          maxStockPct: 50.0,
          slsQty: 2.0,
          stockQty: 0.0,
          suggestedRefillQty: 5.0,
          plannedQty: 9.0,
          maxStockLevel: 5.0,
          userRefillQty: 5.0,
          sellThru: 100.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "KURTA H/S",
          articleNo: "M-110-24",
          colour: "OLIVE",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 5.0,
          plannedQty: 9.0,
          maxStockLevel: 5.0,
          userRefillQty: 5.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "SHIRT H/S",
          articleNo: "M-113-24",
          colour: "GREY",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 6.0,
          plannedQty: 9.0,
          maxStockLevel: 6.0,
          userRefillQty: 6.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "SHIRT H/S",
          articleNo: "M-113-24",
          colour: "MINT",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 4.0,
          plannedQty: 6.0,
          maxStockLevel: 4.0,
          userRefillQty: 4.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "SHIRT H/S",
          articleNo: "M-115-24",
          colour: "DENIM",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 5.0,
          plannedQty: 7.0,
          maxStockLevel: 5.0,
          userRefillQty: 5.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "SHIRT H/S",
          articleNo: "M-115-24",
          colour: "NATURAL",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 6.0,
          plannedQty: 9.0,
          maxStockLevel: 6.0,
          userRefillQty: 6.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "SHIRT H/S",
          articleNo: "M-131-24",
          colour: "KHAKI",
          maxStockPct: 50.0,
          slsQty: 1.0,
          stockQty: 0.0,
          suggestedRefillQty: 5.0,
          plannedQty: 7.0,
          maxStockLevel: 5.0,
          userRefillQty: 5.0,
          sellThru: 100.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "SHIRT H/S",
          articleNo: "M-162-24",
          colour: "CHARCOAL",
          maxStockPct: 50.0,
          slsQty: 1.0,
          stockQty: 0.0,
          suggestedRefillQty: 5.0,
          plannedQty: 7.0,
          maxStockLevel: 5.0,
          userRefillQty: 5.0,
          sellThru: 100.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "WOMEN",
          subSectionName: "DRESS",
          articleNo: "MWD-27-24",
          colour: "BLACK",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 5.0,
          plannedQty: 7.0,
          maxStockLevel: 5.0,
          userRefillQty: 5.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "WOMEN",
          subSectionName: "DRESS",
          articleNo: "MWD-28-24",
          colour: "MASTIC",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 5.0,
          plannedQty: 7.0,
          maxStockLevel: 5.0,
          userRefillQty: 5.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "WOMEN",
          subSectionName: "SHIRT H/S",
          articleNo: "MWS-34-24",
          colour: "IRIS",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 5.0,
          plannedQty: 7.0,
          maxStockLevel: 5.0,
          userRefillQty: 5.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "WOVEN LOWER",
          articleNo: "OL-14-24",
          colour: "BLACK",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 6.0,
          plannedQty: 11.0,
          maxStockLevel: 6.0,
          userRefillQty: 6.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "WOVEN LOWER",
          articleNo: "OL-14-24",
          colour: "GUN METAL",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 6.0,
          plannedQty: 8.0,
          maxStockLevel: 6.0,
          userRefillQty: 6.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "WOVEN LOWER",
          articleNo: "OL-14-24",
          colour: "NAVY",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 6.0,
          plannedQty: 8.0,
          maxStockLevel: 6.0,
          userRefillQty: 6.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "WOVEN SHORTS",
          articleNo: "OS-50-24",
          colour: "BLACK",
          maxStockPct: 50.0,
          slsQty: 2.0,
          stockQty: 0.0,
          suggestedRefillQty: 6.0,
          plannedQty: 9.0,
          maxStockLevel: 6.0,
          userRefillQty: 6.0,
          sellThru: 100.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "WOVEN SHORTS",
          articleNo: "OS-50-24",
          colour: "GUN METAL",
          maxStockPct: 50.0,
          slsQty: 2.0,
          stockQty: 0.0,
          suggestedRefillQty: 6.0,
          plannedQty: 9.0,
          maxStockLevel: 6.0,
          userRefillQty: 6.0,
          sellThru: 100.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "WOVEN SHORTS",
          articleNo: "OS-50-24",
          colour: "WHITE",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 6.0,
          plannedQty: 8.0,
          maxStockLevel: 6.0,
          userRefillQty: 6.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "AIR-FORCE",
          maxStockPct: 50.0,
          slsQty: 1.0,
          stockQty: 0.0,
          suggestedRefillQty: 7.0,
          plannedQty: 10.0,
          maxStockLevel: 7.0,
          userRefillQty: 7.0,
          sellThru: 100.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "BLACK",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 10.0,
          plannedQty: 16.0,
          maxStockLevel: 10.0,
          userRefillQty: 10.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "DARK WINE",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 10.0,
          plannedQty: 16.0,
          maxStockLevel: 10.0,
          userRefillQty: 10.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "LIGHT TEAL",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 7.0,
          plannedQty: 10.0,
          maxStockLevel: 7.0,
          userRefillQty: 7.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "MOCHA",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 7.0,
          plannedQty: 10.0,
          maxStockLevel: 7.0,
          userRefillQty: 7.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "OLIVE",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 7.0,
          plannedQty: 10.0,
          maxStockLevel: 7.0,
          userRefillQty: 7.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "RUST",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 7.0,
          plannedQty: 10.0,
          maxStockLevel: 7.0,
          userRefillQty: 7.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "STONE",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 10.0,
          plannedQty: 16.0,
          maxStockLevel: 10.0,
          userRefillQty: 10.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "SUEDE PINK",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 7.0,
          plannedQty: 10.0,
          maxStockLevel: 7.0,
          userRefillQty: 7.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "TEAL",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 10.0,
          plannedQty: 16.0,
          maxStockLevel: 10.0,
          userRefillQty: 10.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-101-24",
          colour: "WHITE",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 6.0,
          plannedQty: 10.0,
          maxStockLevel: 7.0,
          userRefillQty: 6.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-103-24",
          colour: "KHAKI MELANGE",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 8.0,
          plannedQty: 11.0,
          maxStockLevel: 8.0,
          userRefillQty: 8.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-105-24",
          colour: "BOTTLE GREEN",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 7.0,
          plannedQty: 12.0,
          maxStockLevel: 7.0,
          userRefillQty: 7.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-105-24",
          colour: "MERLOT",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 7.0,
          plannedQty: 12.0,
          maxStockLevel: 7.0,
          userRefillQty: 7.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-105-24",
          colour: "WHITE",
          maxStockPct: 50.0,
          slsQty: 0.0,
          stockQty: 0.0,
          suggestedRefillQty: 7.0,
          plannedQty: 12.0,
          maxStockLevel: 7.0,
          userRefillQty: 7.0,
          sellThru: 0.0,
          daysOfStock: 0.0,
        },
        {
          sectionName: "MEN",
          subSectionName: "T-SHIRT H/S",
          articleNo: "S-320-24",
          colour: "LIGHT NAVY",
          maxStockPct: 50.0,
          slsQty: 4.0,
          stockQty: 0.0,
          suggestedRefillQty: 6.0,
          plannedQty: 8.0,
          maxStockLevel: 6.0,
          userRefillQty: 6.0,
          sellThru: 100.0,
          daysOfStock: 0.0,
        },
      ],
    };
  },

  mounted() {
    console.log("Items data", this.items);
  },
};
</script>
