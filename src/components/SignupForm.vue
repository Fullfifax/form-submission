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
    </form>
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: 'developer'
        }
    }
}
</script>

<style>
    form {
        background-color: #81dd75;
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
</style>