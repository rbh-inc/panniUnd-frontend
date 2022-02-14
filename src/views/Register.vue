<template>
  <div class="container">
    <div class="heading">
      <h3>Worker Form Submission</h3>
    </div>
    <div class="form">
      <form @submit.prevent="onSubmit">
        <div class="dpSection">
          <img
            src="https://img.icons8.com/external-linector-flat-linector/100/000000/external-avatar-man-avatar-linector-flat-linector-6.png"
          />
          <input
            class="fileUpload-btn"
            type="file"
            id="displayPicture"
            name="displayPicture"
            accept="image/*"
          />
        </div>

        <div class="gender-section">
          <p>Sex</p>

          <div>
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
        </div>

        <div class="label-input">
          <label class="label-text" for="name"> Name </label>
          <input
            class="input-text"
            v-model="form.name"
            type="text"
            id="name"
            name="name"
            placeholder="John"
          />
        </div>

        <div class="label-input">
          <label class="label-text" for="description"> Description </label>
          <textarea
            class="input-text"
            v-model="form.description"
            type="text"
            id="description"
            name="description"
            placeholder="describe your past jobs and work experiences"
          ></textarea>
        </div>

        <div class="label-input">
          <label for="phoneNo"> Phone No </label>
          <input
            v-model="form.phoneNo"
            type="number"
            id="phoneNo"
            name="phoneNo"
            placeholder=""
            min="0"
          />
        </div>

        <div class="label-input">
          <label for="adharNo"> Adhar No </label>
          <input
            v-model="form.adharNo"
            type="number"
            id="adharNo"
            name="adharNo"
            placeholder=""
          />
        </div>

        <div class="label-input">
          <label for="sector"> Sector </label>
          <input
            v-model="form.sector"
            type="text"
            id="sector"
            name="sector"
            placeholder=""
          />
        </div>

        <div class="label-input">
          <label for="subSector"> Sub Sector </label>
          <input
            v-model="form.subSector"
            type="text"
            id="subSector"
            name="subSector"
            placeholder=""
          />
        </div>

        <div class="label-input">
          <label for="skill">Skill </label>
          <input
            v-model="form.skill"
            type="text"
            id="skill"
            name="skill"
            placeholder="optional"
          />
        </div>

        <div class="label-input">
          <label for="hourlyRate"> Hourly Rate </label>
          <input
            v-model="form.hourlyRate"
            type="number"
            id="hourlyRate"
            name="hourlyRate"
            placeholder=""
          />
        </div>

        <div class="label-input">
          <label for="place"> Place </label>
          <input
            v-model="form.place"
            type="text"
            id="place"
            name="place"
            placeholder=""
          />
        </div>

        <div class="label-input">
          <label for="district"> State </label>
          <input
            v-model="form.state"
            type="text"
            id="state"
            name="state"
            placeholder=""
          />
        </div>

        <button class="submit-btn">Submit</button>
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
            alert("submission succuss");
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
.heading {
  text-align: center;
  font-size: 20px;
}

.form {
  font-family: "Poppins", sans-serif;
  font-weight: 500;
  max-width: 700px;
  margin: 20%;
  margin-top: 20px;
  font-size: 20px;
}

.dpSection {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.dpSection img {
  width: 200px;
  border-radius: 100px;
}
.fileUpload-btn {
  border: 1px solid #ccc;
  border-radius: 4px;
  margin: 10px;
  display: inline-block;
  padding: 6px 12px;
  cursor: pointer;
}

.gender-section {
  margin: 10px;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
}
.gender-section input {
  margin-left: 40px;
}

.label-input {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 10px;
}
.label-input input {
  width: 75%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  font-size: 15px;
}
.label-input textarea {
  width: 75%;
  height: 120px;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  font-size: 15px;
  resize: none;
}
.label-input label {
  margin-right: 15px;
}

.submit-btn {
  border: none;
  margin: 10px;
  padding: 10px 22px;
  font-weight: bold;
  font-size: 20px;
  background-color: #42b983;
  color: white;
}

/* remove number input=type=number couting arrows Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
/* Firefox */
input[type="number"] {
  -moz-appearance: textfield;
}

@media only screen and (max-width: 1000px) {
  /*Small smartphones [325px -> 425px]*/
  .form {
    margin: 10%;
    font-size: 20px;
  }
}
@media only screen and (max-width: 550px) {
  /*Small smartphones [325px -> 425px]*/
  .form {
    margin: 2%;
    font-size: 18px;
  }
}
</style>