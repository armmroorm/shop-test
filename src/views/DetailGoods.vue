<template>
  <div>
    <v-container>
      <v-row no-gutters>
        <v-col cols="12" sm="9">
          <span class="display-1 hidden-sm-and-up">{{
            DetailProduct.name_product
          }}</span>
          <v-card>
            <v-container fluid>
              <v-row>
                <v-col
                  v-for="(path, index) in DetailProduct.images"
                  :key="index"
                  class="d-flex child-flex"
                  cols="6"
                >
                  <v-card flat tile class="d-flex" @click="eventDialog(index)">
                    <v-img :src="path" aspect-ratio="1" class="grey lighten-2">
                      <template v-slot:placeholder>
                        <v-row
                          class="fill-height ma-0"
                          align="center"
                          justify="center"
                        >
                          <v-progress-circular
                            indeterminate
                            color="grey lighten-5"
                          ></v-progress-circular>
                        </v-row>
                      </template>
                    </v-img>
                  </v-card>
                </v-col>
              </v-row>
            </v-container>
          </v-card>
        </v-col>
        <!--  -->
        <v-col cols="12" sm="3" class="pa-3">
          <v-row no-gutters>
            <v-col cols="6" sm="6" align="left"
              ><span class="subtitle-2"
                >{{ DetailProduct.tags[0] }}
              </span></v-col
            >
            <v-col cols="6" sm="6" align="right"
              ><span>{{ DetailProduct.price | currency("$") }} </span></v-col
            >
            <v-col cols="12" align="left"
              ><span class="headline"
                >{{ DetailProduct.name_product }}
              </span></v-col
            >
          </v-row>
          <v-row>
            <v-col cols="6" align="left"
              ><span class="subtitle-2">Sizes</span></v-col
            >
            <v-row no-gutters>
              <v-col cols="3" v-for="(size, index) in sizes" :key="index">
                <v-col>
                  <v-btn-toggle color="deep-orange accent-3" rounded>
                    <v-btn value="center" width="60">{{ size.name }}</v-btn>
                  </v-btn-toggle>
                </v-col>
              </v-col>
            </v-row>
            <v-col cols="12">
              
              <add-to-cart
                :name="DetailProduct.name_product"
                :price="DetailProduct.price"
                :pId="DetailProduct.id"
                :image="DetailProduct.images[0]"
              />
            </v-col>
            <v-col cols="12">
              <span v-html="DetailProduct.description"></span>
            </v-col>
            <v-col cols="12">
              <v-btn text class="subtitle-2 u" @click="dialog1 = true">
                <u>Detail</u>
              </v-btn>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
    <!--  -->
    <v-dialog
      v-model="dialog1"
      fullscreen
      hide-overlay
      transition="dialog-bottom-transition"
    >
      <v-card>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="red darken-1" text @click="dialog1 = false"
            ><v-icon>mdi-close-circle</v-icon></v-btn
          >
        </v-card-actions>
        <v-container>
          <v-card-text>
            <span class="display-1"
              >{{ DetailProduct.name_product || name }}
            </span>
            <p class="subtitle-1">
              ลดแรงกระแทกไม่หยุดตลอดเส้นทาง
            </p>
            <p class="subtitle-1">
              Nike React Infinity Run Flyknit
              ดีไซน์มาเพื่อช่วยลดอาการบาดเจ็บและให้คุณวิ่งได้อย่างต่อเนื่อง
              มาพร้อมโฟมที่มากขึ้นและรายละเอียดส่วนบนที่พัฒนาขึ้น
              เพื่อให้สัมผัสที่แน่นกระชับและลดแรงกระแทกได้ดี
              ผูกเชือกแล้วสัมผัสถึงศักยภาพของคู่นี้เมื่อออกลุยบนถนนได้เลย
            </p>
            <p class="subtitle-1">
              ทรงน้ำหนักเบา Flyknit
              รุ่นใหม่แกะกล่องทั้งแข็งแรงขึ้นและทนทานยิ่งกว่ารุ่นก่อนๆ ที่ผ่านมา
              โดยมีน้ำหนักเบาและยืดหยุ่น โดดเด่นด้วยเลเยอร์ที่แตกต่างกัน 3
              ชั้นเพื่อช่วยให้เท้าของคุณแน่นกระชับอยู่เสมอ
            </p>
            <div class="text--primary">
              <span class="subtitle-1">ข้อดีเพิ่มเติม</span>
              <ul class="subtitle-1">
                <li>
                  วัสดุระหว่างพื้นรองเท้าชั้นในและพื้นรองเท้าชั้นกลางใช้น้อยลง
                  คุณจึงแนบชิดกับโฟมได้มากขึ้น
                  และทำให้เกิดประสบการณ์ที่นุ่มกว่าและตอบสนองได้ดียิ่งกว่าที่เคย
                </li>
                <li>
                  พื้นรองเท้าชั้นนอกมีปริมาณยางมากขึ้น
                  จึงช่วยยึดเกาะและให้ความทนทาน
                </li>
              </ul>
            </div>
            <div class="text--primary">
              <span class="subtitle-1">รายละเอียดสินค้า</span>
              <ul class="subtitle-1">
                <li>
                  น้ำหนัก: 10.27 ออนซ์ (รองเท้าผู้ชายไซส์ 10)
                </li>
                <li>
                  ออฟเซ็ต: 9 มม. (ปลายเท้า 24 มม., ส้น 33 มม.)
                </li>
                <li>
                  สีที่แสดง: Sail/Track Red/Laser Orange/Black
                </li>
              </ul>
            </div>
          </v-card-text>
        </v-container>
      </v-card>
    </v-dialog>
    <!--  -->
    <v-dialog v-model="dialog">
      <v-card>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="red darken-1" text @click="dialog = false"
            ><v-icon>mdi-close-circle</v-icon></v-btn
          >
        </v-card-actions>
        <v-img :src="setImg" max-height="600" contain> </v-img>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  computed: {
    ...mapGetters({ DetailProduct: "store/DetailProduct" })
  },
  methods: {
    eventDialog(index) {
      console.log(index);
      this.setImg = this.DetailProduct.images[index];
      this.dialog = true;
    }
  },
  data() {
    return {
      products: [],
      name: "Nike Air Max 2090",
      price: 5000,
      dialog: false,
      dialog1: false,
      type: "Men",
      setImg: "",
      sizes: [
        { name: "5" },
        { name: "5.5" },
        { name: "6" },
        { name: "6.5" },
        { name: "7" },
        { name: "7.5" },
        { name: "8" },
        { name: "8.5" },
        { name: "9 " },
        { name: "9.5" },
        { name: "10" },
        { name: "10.5" },
        { name: "11" },
        { name: "11.5" },
        { name: "12" },
        { name: "12.5" },
        { name: "13" },
        { name: "14" },
        { name: "15" },
        { name: "16" },
        { name: "17" }
      ]
      // path: [
      //   {
      //     img: require("@/assets/CO/Untitled-1.png"),
      //   },
      // ],
    };
  }
};
</script>

<style></style>
