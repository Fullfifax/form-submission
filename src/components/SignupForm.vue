<template>
    <form @submit.prevent="handleSubmit">
        <h2>Test form submission with Vue ;)</h2>
        <label>Email:</label>
        <input type="email" required v-model="email">

        <label>Password:</label>
        <input type="password" required v-model="password">
        <p v-ipsswd-errorf="passwordError" class="psswd-error">{{ passwordError }}</p>
        
        <label>Role:</label>
        <select v-model="role">
            <option value="developer">Web developer</option>
            <option value="design">Web designer</option>
        </select>

        <label>Skills (press alt + comma (,) to add new skill)</label>
        <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
        <div class="pill">
            <p v-for="skill in skills" :key="skills" @click="deleteSkill(skill)">{{ skill }}</p>
        </div>

        <div class="terms">
            <input type="checkbox" required v-model="terms">
            <label>Accept terms and conditions</label>
        </div>

        <div class="submit">
            <button>Submit form</button>
        </div>
        <!--psswd-error
        <div class="names">
            <h2>Who do you prefer ?</h2>
            <div>
                <input type="checkbox" value="Fullfifax" v-model="names">
                <label>Fullfifax</label>
            </div>
            <div>
                <input type="checkbox" value="Full" v-model="names">
                <label>Full</label>
            </div>psswd-error
            <div>
                <input type="checkbox" value="Fifax" v-model="names">
                <label>Fifax</label>
            </div>
        </div>
        -->
    </form>
    <p>Email: {{ email }}</p>
    <p>Passworpsswd-errord: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Terms: {{ terms }}</p>
    <p>Skills: {{ skills }}</p>
    <!--
    <p>Names: {{ names }}</p>
    -->
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: 'developer',
            terms: false,
            tempSkill: '',
            skills: [],
            passwordError: ''
            // names: []
        }
    },
    methods: {
        addSkill(e) {
            if(e.key === ',' && this.tempSkill) {
                if(!this.skills.includes(this.tempSkill)) {
                    this.skills.push(this.tempSkill)
                } 
                this.tempSkill = ''
            }
        },
        deleteSkill(skill) {
            this.skills = this.skills.filter((item) => {
                return skill !== item
            })
        },
        handleSubmit() {
            this.passwordError = this.password.length > 5 ? '' : 'Password must be at least 6 characters'

            // Tests
            if(!this.passwordError) {
                console.log('email: ', this.email)
                console.log('password: ', this.password)
                console.log('role: ', this.role)
                console.log('skills: ', this.skills)
                console.log('terms: ', this.terms)
            }
        }
    }
}
</script>

<style>
    form {
        background-color: #81dd75;
        border-radius: 20px;
        margin: 30px auto;
        max-width: 420px;
        padding: 0 60px 20px;
        text-align: left;
    }
    label {
        color: white;
        display: inline-block;
        font-size: 1em;
        margin: 25px 0 15px;
    }
    input, select {
        background-color: #81dd75;
        border: none;
        border-bottom: 1px solid white;
        color: white;
        font-size: 1.1em;
        display: block;
        padding: 10px 6px;
        width: 100%;
    }
    input:focus {
        border: none;
    }
    input[type="checkbox"] {
        display: inline-block;
        margin-right: 10px;
        position: relative;
        width: 16px;
    }
    .pill {
        display: flex;
        flex-wrap: wrap;
    }
    .pill p {
        background-color: white;
        border-radius: 20px;
        color: #81dd75;
        cursor: pointer;
        font-size: 1em;
        font-weight: bold;
        margin: 1em 1em 0 0;
        padding: 8px 16px;
    }
    .submit button {
        background-color: #5dc74f;
        border: none;
        border-radius: 16px;
        color: white;
        cursor: pointer;
        font-weight: bold;
        padding: 12px 16px;
        text-transform: uppercase;
        width: 100%;
    }
    .psswd-error {
        color: rgb(221, 75, 75);
    }
    form h2 {
        color: white;
        padding-top: 2em;
        text-align: center;
    }
</style>