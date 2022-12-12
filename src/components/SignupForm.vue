<template>
    <form>
        <label>Email:</label>
        <input type="email" required v-model="email">

        <label>Password:</label>
        <input type="password" required v-model="password">

        <label>Role:</label>
        <select v-model="role">
            <option value="developer">Web developer</option>
            <option value="design">Web designer</option>
        </select>

        <label>Skills (press Enter to add new skill)</label>
        <input type="text" v-model="tempSkill" @keyup="addSkill">
        <div class="pill">
            <p v-for="skill in skills" :key="skills" @click="deleteSkill(skill)">{{ skill }}</p>
        </div>

        <div class="terms">
            <input type="checkbox" required v-model="terms">
            <label>Accept terms and conditions</label>
        </div>

        <!--
        <div class="names">
            <h2>Who do you prefer ?</h2>
            <div>
                <input type="checkbox" value="Fullfifax" v-model="names">
                <label>Fullfifax</label>
            </div>
            <div>
                <input type="checkbox" value="Full" v-model="names">
                <label>Full</label>
            </div>
            <div>
                <input type="checkbox" value="Fifax" v-model="names">
                <label>Fifax</label>
            </div>
        </div>
        -->
    </form>
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
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
            skills: []
            // names: []
        }
    },
    methods: {
        addSkill(e) {
            if(e.key === 'Enter' && this.tempSkill) {
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
        font-size: 1.2em;
        margin: 25px 0 15px;
    }
    input, select {
        border: none;
        color: #555;
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
        font-size: 1em;
        font-weight: bold;
        margin: 1em 1em 0 0;
        padding: 8px 16px;
    }
</style>