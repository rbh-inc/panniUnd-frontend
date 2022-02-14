<template>
  <div class="container">
    <div class="heading">
      <h3>submit your skill and get a work</h3>
    </div>
    <div class="form">
      <form @submit.prevent="onSubmit">
        <div class="form-top">
          <div>
            <img
              src="https://img.icons8.com/external-linector-flat-linector/100/000000/external-avatar-man-avatar-linector-flat-linector-6.png"
            />
            <input
              type="file"
              id="displayPicture"
              name="displayPicture"
              accept="image/*"
            />
            <span>img submission not supported</span>

            <p><sup>*</sup>Sex:</p>

            <input
              v-model="form.sex"
              type="radio"
              id="male"
              name="sex"
              value="male"
            />
            <label for="male"> Male</label>

            <input
              v-model="form.sex"
              type="radio"
              id="female"
              name="sex"
              value="female"
            />
            <label for="female"> Female</label>

            <input
              v-model="form.sex"
              type="radio"
              id="other"
              name="sex"
              value="other"
            />
            <label for="other"> Other</label>
          </div>

          <div>
            <label for="name"><sup>*</sup> Name: </label>
            <input
              v-model="form.name"
              type="text"
              id="name"
              name="name"
              placeholder="John"
            /><br />

            <label for="description"><sup>*</sup> Description: </label>
            <textarea
              v-model="form.description"
              type="text"
              id="description"
              name="description"
              placeholder="describe your past jobs and work experiences"
            ></textarea>
          </div>
        </div>

        <div class="form-mid">
          <label for="phoneNo"><sup>*</sup> Phone No: </label>
          <input
            v-model="form.phoneNo"
            type="number"
            id="phoneNo"
            name="phoneNo"
            placeholder=""
            min="0"
          /><br />

          <label for="adharNo"><sup>*</sup> Adhar No: </label>
          <input
            v-model="form.adharNo"
            type="number"
            id="adharNo"
            name="adharNo"
            placeholder=""
          /><br />

          <label for="sector"><sup>*</sup> Sector: </label>
          <input
            v-model="form.sector"
            type="text"
            id="sector"
            name="sector"
            placeholder=""
          /><br />

          <label for="subSector"><sup>*</sup> Sub Sector: </label>
          <input
            v-model="form.subSector"
            type="text"
            id="subSector"
            name="subSector"
            placeholder=""
          /><br />

          <label for="skill">Skill : </label>
          <input
            v-model="form.skill"
            type="text"
            id="skill"
            name="skill"
            placeholder="optional"
          /><br />
        </div>

        <div class="form-end">
          <label for="hourlyRate"><sup>*</sup> Hourly rate: </label>
          <input
            v-model="form.hourlyRate"
            type="number"
            id="hourlyRate"
            name="hourlyRate"
            placeholder=""
          /><br />

          <label for="place"><sup>*</sup> Place: </label>
          <input
            v-model="form.place"
            type="text"
            id="place"
            name="place"
            placeholder=""
          /><br />

          <label for="district"><sup>*</sup> State: </label>
          <input
            v-model="form.state"
            type="text"
            id="state"
            name="state"
            placeholder=""
          /><br />
        </div>
        <button>Submit</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Register",
  data() {
    return {
      form: {
        name: "",
        description: "",
        sex: "",
        dpUrl: "not working for now",
        phoneNo: null,
        adharNo: null,
        sector: "",
        subSector: "",
        skill: "",
        hourlyRate: null,
        place: "",
        state: "",
      },
    };
  },
  methods: {
    onSubmit() {
      console.log("submited");
      fetch(`https://panniapp.herokuapp.com/registerWorker`, {
        method: "POST", //This could be any http method
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(this.form),
      })
        .then((response) => response.json())
        .then((success) => {
          if (success.statusCode) {
            alert("fill all the forms correctly");
          } else {
            console.log(success);
          }
        })
        .catch((e) => {
          console.error(e);
        });
    },
  },
};
</script>

<style scoped>
.container {
  margin: 2% 4%;
}
</style>