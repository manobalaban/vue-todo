<template>
    <modal ref="modal">
        <form class="app-form">
            <div class="form-control">
                <label class="label">Title</label>
                <input 
                    v-model="form.title"
                    class="form-input" 
                    type="text">
            </div>
            <div class="form-control form-control-last">
                <label class="label">Description</label>
                <textarea
                    v-model="form.description"
                    cols="30"
                    rows="5"
                    class="form-input" >
                </textarea>
            </div>
            <div class="app-error">
                <div class="form-error">
                    {{formError}}
                </div>
            </div>
            <button 
                @click="submitForm"
                type="button" 
                class="app-button is-primary">Confirm</button>
        </form>
    </modal>
</template>

<script>
import modal from '@/components/modal'
export default {
    components: {
        modal
    },
    
    data() {
        return {
            form: {
                title: '',
                description: ''
            },
            formError: ''
        }
    },

    computed: {
        isFormValid() {
            return this.form.title.length > 8 && this.form.description.length > 10 ? true : false
        },

        modal() {
            return this.$refs.modal
        }
    },

    methods: {
        submitForm() {
            if (this.isFormValid) {
                this.formError = ''
                this.$emit('formSubmitted', {...this.form})
                this.modal.close()
                this.resetForm()
            } else {
                this.formError = 'Form Error! Title min 8, description min 10'
            }
        },
        resetForm() {
            this.form.title = ''
            this.form.description = ''
        }
    }
}
</script>

<style lang="scss" scoped>
    .form-error {
        margin-bottom:10px;
    }

    .app-error {
        color: #ff1212;
    }

</style>