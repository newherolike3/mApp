<template>
  <section>
    <img :src="picture" :width="size" :height="size" ref="imageEl" /><br />
    <h1>ชื่อ-นามสกุล : {{ getFullName }}</h1>
    <h1>อายุ : {{ age }} ปี</h1>
    
    <h1>อาชีพ : {{getDepartment}}</h1>
    
    <button @click="toggleVisible">{{ isVisible ? "ซ่อน" : "แสดง"}}รายละเอียด</button>
    <article v-show="isVisible">
      <p>ที่อยู่ : <span v-html="address"></span></p>
      <p>Social : <a :href="social" target="_blank">Facebook</a></p>
      <p v-if="hobby.length === 0">ไม่มีงานอดิเรก</p>
      <div v-else>
        <p>งานอดิเรก :</p>
        <ul>
          <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
        </ul>
      </div>
      <p>ข้อมูลพื้นฐาน :</p>
      <ul>
        <li v-for="(item, key) in general" :key="key">{{ item }}</li>
      </ul>
    </article>
  </section>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstName: "Natdanai",
      lastName: "Tinnakon",
      age: 22,
      address: "<i>พิจิตร</i>",
      picture:"https://scontent.fphs2-1.fna.fbcdn.net/v/t1.6435-9/110320079_678019732751735_1561759245512041012_n.jpg?_nc_cat=111&ccb=1-5&_nc_sid=174925&_nc_ohc=eOn8pnYN7OEAX-pzauM&tn=G-cp_SvtvjVsKRCP&_nc_ht=scontent.fphs2-1.fna&oh=00_AT-BjzAgerOiEDbamU-rPbGnsyhpF2O3pfUkKGRHi5pCAg&oe=62380005",
      size: 150,
      social: "https://www.facebook.com/newz.natdanai.12/",
      hobby: [
        "ฟังเพลง",
        "เล่นเกม",
        "ดูทีวี",
        "ท่องเน็ต",
        "อ่านหนังสือ",
        
      ],
      general: { gender: "ชาย", weight: 100, height: 170, status: false },
      isVisible:false,
      
    };
  },
  methods: {
    toggleVisible(){
        this.isVisible = !this.isVisible
    },
    addSalary(value){
        this.salary+=value
    }
  },
  computed:{
    getFullName() {
        return `${this.firstName}  ${this.lastName}`;
    },
    getIncome(){
        return this.salary * 12;
    },
    getDepartment(){
        return this.salary >=35000 ? "Project manager" : "นักศึกษา"
    }
  },
  
  
};
</script>

<style></style>