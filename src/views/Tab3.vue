<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>ลูกค้า</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">

      <ion-button @click="addCustomer" color="success" size="small">เพิ่มข้อมูลลูกค้า</ion-button>

      <ion-list>
        <ion-item>
          <ion-label>ชื่อ - นามสกุล : </ion-label>
          <ion-input v-model="name" autofocus="true"></ion-input>
        </ion-item>
        <ion-item>
          <ion-label>เบอร์โทรศัพท์ : </ion-label>
          <ion-input v-model="tel"></ion-input>
        </ion-item>
      </ion-list>

      <ion-list>
        <ion-item-sliding>
          <ion-item>
            <ion-avatar slot="start">
              <img src="../../public/assets/icon/icon.png" />
            </ion-avatar>
            <ion-label>นายณัฐดนัย ทินกร</ion-label>
          </ion-item>
          <ion-item-options slot="end">
            <ion-item-option>เพิ่มเติม</ion-item-option>
          </ion-item-options>
        </ion-item-sliding>
        <ion-item-sliding>
          <ion-item>
            <ion-avatar slot="start">
              <img src="../../public/assets/icon/icon.png" />
            </ion-avatar>
            <ion-label>นายเทพ ดวงดี </ion-label>
          </ion-item>
          <ion-item-options slot="end">
            <ion-item-option>เพิ่มเติม</ion-item-option>
          </ion-item-options>
        </ion-item-sliding>
        <ion-item-sliding>
          <ion-item>
            <ion-avatar slot="start">
              <img src="../../public/assets/icon/icon.png" />
            </ion-avatar>
            <ion-label>นางสาวสมหญิง วันจันทร์</ion-label>
          </ion-item>
          <ion-item-options slot="end">
            <ion-item-option>เพิ่มเติม</ion-item-option>
          </ion-item-options>
        </ion-item-sliding>
      </ion-list>

      <!-- <ion-list>
        <ion-item>
          <ion-label>ชื่อ - นามสกุล : </ion-label>
          <ion-input></ion-input>
        </ion-item>
        <ion-item>
          <ion-label>เบอร์โทรศัพท์ : </ion-label>
          <ion-input></ion-input>
        </ion-item>
        <ion-item>
          <ion-label>เสียงแจ้งเตือน</ion-label>
          <ion-toggle slot="end"></ion-toggle>
        </ion-item>
        <ion-item>
          <ion-label>GPS</ion-label>
          <ion-toggle slot="end"></ion-toggle>
        </ion-item>
        <ion-item>
          <ion-label>Radio 1</ion-label>
          <ion-radio slot="start"></ion-radio>
        </ion-item>
        <ion-item>
          <ion-label>Radio 2</ion-label>
          <ion-radio slot="start"></ion-radio>
        </ion-item>
        <ion-item>
          <ion-label>Checkbox 1</ion-label>
          <ion-checkbox slot="end"></ion-checkbox>
        </ion-item>
        <ion-item>
          <ion-label>Checkbox 2</ion-label>
          <ion-checkbox slot="end"></ion-checkbox>
        </ion-item>
      </ion-list> -->

    </ion-content>
  </ion-page>
</template>

<script>
import { alertController, IonButton, IonItemOption, IonItemOptions, IonItemSliding, IonAvatar, IonInput, IonList, IonItem, IonLabel, IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import axios from 'axios';

export default  {
  name: 'Tab3',
  components: { IonButton ,IonItemOption, IonItemOptions, IonItemSliding, IonAvatar, IonInput, IonList, IonItem, IonLabel, IonHeader, IonToolbar, IonTitle, IonContent, IonPage },
  data(){
    return {
      name: "",
      tel: ""
    }
  },
  methods: {
    clearInput(){
      this.name = "";
      this.tel = "";
    },
    async addCustomer(){

      if(this.name.trim() !== "" && this.tel.trim() !== ""){
        // console.log("เพิ่มข้อมูลลูกค้า");
        // console.log(this.name.trim());
        // console.log(this.tel.trim());
        try {
          const res = await axios.post("http://localhost:3000/mongo/customers", {
            name: this.name.trim(),
            tel: this.tel.trim()
          });

          this.clearInput();

          const alert = await alertController.create({
            header: "สำเร็จ",
            message: res.data.message,
            buttons: ['OK']
          });

          await alert.present();

        } catch (error) {
          console.log(error);
        }

      } else {

        const alert = await alertController.create({
          header: "คำเตือน",
          message: "กรุณากรอกข้อมูลให้ครบถ้วน",
          buttons: ['OK']
        });

        await alert.present();

      }

    }
  }
}
</script>