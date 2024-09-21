<script setup>
import { reactive } from 'vue';
let formData = reactive({
    firstname: '',
    lastname: '',
    age: 0,
    gender: '',
    interests: [],
    description: '',
});

const gendersList = ['ชาย', 'หญิง', 'ได้หมด', 'สดชื่น'];
const interestsList = ['ฟุตบอล', 'ปิงปอง', 'แบต'];

const submitData = () => {
    console.log('formData', JSON.parse(JSON.stringify(formData)));
    console.log('interest', formData.interests.join())
};
</script>

<template>
    <div class="container">
        <div>
            <label>ชื่อจริง</label><input type="text" v-model="formData.firstname" />
        </div>
        <div>
            <label>นามสกุล</label><input type="text" v-model="formData.lastname" />
        </div>
        <div><label>อายุ</label><input type="number" v-model="formData.age" /></div>
        <div>
            <div>เพศ</div>
            <div v-for="gender in gendersList">
                <input type="radio" :value="gender" v-model="formData.gender" />{{
                    gender
                }}
            </div>
        </div>
        <div>
            <div>เพศ</div>
            <div v-for="interests in interestsList">
                <input type="checkbox" :value="interests" v-model="formData.interests" />{{ interests }}
            </div>
        </div>
        <div>
            <textarea v-model="formData.description"></textarea>
        </div>
        <div>
            <button @click="submitData">submit</button>
        </div>
    </div>
</template>

<style>
.container {
    width: 100%;
    margin: 0;
}
</style>
