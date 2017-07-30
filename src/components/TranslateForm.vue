<template>
  <div id="translateForm" class="row">
  <div class="col-md-4 col-md-offset-4">
    <form id="transForm" v-on:submit="formSubmit">
        <div class="form-group">   
            <input 
                type="text" 
                class="form-control"
                v-model="textToTranslate" 
                placeholder="Enter a Word ...">
            </div> 
        <div class="form-group">  
            <select class="form-control" id="langChange" v-model="language">
                <option value="en">English</option>
                <option value="ru">Russian</option>
                <option value="es">Spanish</option>
                <option value="fr">French</option>
                <option value="de">German</option>
            </select>
        </div>
        <div class="form-group">  
            <input type="submit" id="submit" class="btn btn-block btn-success" value="Translate">
        </div>
    </form>
  </div>
   
  </div>
</template>

<script>
  export default {
    name: 'translateForm',
    data() {
        return {
            textToTranslate: '',
            language: ''
        }
    },
    created() {
        this.language = 'en';
    },
    methods: {
        formSubmit(e) {
            this.$emit('formSubmit', this.textToTranslate, this.language);
            e.preventDefault();
        }
    }
  }
</script>

<style>
    #transForm {
        border-radius: 10px;
        border: 1px solid #ccc;
        padding: 30px 30px 0 30px;
        box-shadow: 0 1px 10px #000;
        background: #607d8b;
    }

    #transForm input, #langChange {
        font-size: 18px;
    }

    input#submit {
        border-bottom: none;
        transition: background .5s ease-out;
    }

    input#submit:hover {
        background: #2e7d32 ;
        transition: background .7s ease-out;

    }
</style>
