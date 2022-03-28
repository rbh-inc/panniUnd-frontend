<template>
  <div class="container">
    <div class="heading">
      <h3>Worker Form Submission</h3>
    </div>
    <div class="form">
      <form @submit.prevent="onSubmit">
        <div class="dpSection">
          <img src="../assets/avathar-icon.png" />
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
          <select v-model="form.sector" class="select-dropdown">
            <option
              v-for="(value, sector, index) in sectorsSubSectors"
              :key="index"
              :value="sector"
            >
              {{ sector }}
            </option>
          </select>
        </div>

        <div class="label-input">
          <label for="subSector"> Sub Sector </label>
          <select v-model="form.subSector" class="select-dropdown">
            <option
              v-for="(subSector, index) in sectorsSubSectors[form.sector]"
              :key="index"
              :value="subSector"
            >
              {{ subSector }}
            </option>
          </select>
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
        <span id="feedback-text"
          ><i>{{ feedback }}</i></span
        >
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Register",
  data() {
    return {
      feedback: "",
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
      sectorsSubSectors: {
        "Textile and Apparels": [
          "Cutting Master",
          "Button operator",
          "Trimming staff",
          "Finishing Helper",
          "Machine Mechanic",
          "Qc checker",
          "Button hole operator",
          "Iron machine operators",
          "Tailor",
          "Helper",
        ],
        "Food and Dining": [
          "Chef",
          "Waiter",
          "Receptionist",
          "Sous chef",
          "Commi chef",
          "Indian chef",
          "Chinese chef",
          "Arabic chef",
          "Continental chef",
        ],
        "Healthcare and Wellness": [
          "Nurse",
          "Physiotherapist",
          "Nutritionist",
          "Psychiatrist",
          "Optometrist",
          "Pharmacist",
          "Doctor",
          "Lab technician",
          "OT assistant",
          "Ambulance driver",
          "Home nurse",
        ],
        Education: [
          "Subject experts",
          "Lab assistant",
          "Trainer",
          "Mentor",
          "Professor",
        ],
        "Computer and Mobile": [
          "Computer technician",
          "Mobile technician",
          "Software developer",
          "Graphic designer",
        ],
        "Home care Service": [
          "Electrician",
          "Plumber",
          "Carpenter",
          "Mason",
          "Gardener",
          "Home maid",
          "Painter",
          "Flooring",
        ],
        Automobile: [
          "Car mechanic",
          "Puncture repair",
          "Car painting",
          "Car denting work",
          "Car wash",
          "Detailing ",
          "Ceramic coating",
        ],
      },
    };
  },
  methods: {
    onSubmit() {
      this.feedback = "saving user info.";
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
            // alert("fill all the forms correctly");
            this.feedback = "fill all the data correctly.";
          } else {
            console.log(success);
            this.feedback = "successfully saved.";

            // alert("worker data saved.");
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
  margin: 4% 20%;
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
.select-dropdown {
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 75%;
  padding: 12px 20px;
  margin: 8px 0;
  background-color: #fff;
  font-size: 15px;
}

#feedback-text {
  color: #f05454;
  font-weight: 800;
  margin-left: 10px;
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

/* down arrow in selection sector and subsector */
/* Firefox */
input[type="number"] {
  -moz-appearance: textfield;
}
select {
  -moz-appearance: none; /* Firefox */
  -webkit-appearance: none; /* Safari and Chrome */
  appearance: none;
  background-image: url("data:image/svg+xml;utf8,<svg fill='black' height='24' viewBox='0 0 24 24' width='24' xmlns='http://www.w3.org/2000/svg'><path d='M7 10l5 5 5-5z'/><path d='M0 0h24v24H0z' fill='none'/></svg>");
  background-repeat: no-repeat;
  background-position-x: 100%;
  background-position-y: 3px;
}

@media only screen and (max-width: 1000px) {
  /*Small smartphones [325px -> 425px]*/
  .form {
    margin: 1% 10%;
    font-size: 20px;
  }
}
@media only screen and (max-width: 550px) {
  /*Small smartphones [325px -> 425px]*/
  .form {
    margin: 0 2%;
    font-size: 18px;
  }
}
</style>