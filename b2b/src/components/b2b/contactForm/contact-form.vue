<script setup>
    import sendIcon from '../../../assets/images/sendIcon.svg'
</script>

<template>
    <div class="contact-form">
        <div class="contact-form__container container">
            <div class="contact-form__title">
                <h2 class="contact-form__title-main title">
                    Напишите нам <br />
                    и мы перезвоним
                </h2>
                <p class="contact-form__subtitle subtitle">
                    Торговая площадка B2B Search Engine — предоставит вам личного
                    менеджера, который ответит на все ваши вопросы.
                </p>
            </div>

            <div class="contact-form__body">
                <form class="contact-form__form" @submit.prevent="submitForm">
                    <div class="contact-form__fields">
                        <div class="contact-form__field-group">
                            <div class="contact-form__field">
                                <input type="text" id="name" name="name" class="contact-form__input"
                                    placeholder="Ваше имя" v-model="formData.name" required />
                                <!-- <img src="../../assets/i1.svg" alt="" class="contact-form__icon" /> -->
                            </div>
                            <div class="contact-form__field">
                                <input type="tel" id="phone" name="phone" class="contact-form__input"
                                    pattern="[0-9]{10,12}" placeholder="Номер телефона" v-model="formData.phone"
                                    required />
                                <!-- <img src="../../assets/i2.svg" alt="image" class="contact-form__icon" /> -->
                            </div>
                            <div class="contact-form__field">
                                <input type="email" id="email" name="email" class="contact-form__input"
                                    placeholder="Электронная почта" v-model="formData.email" required />
                                <!-- <img src="../../assets/i3.svg" alt="image" class="contact-form__icon" /> -->
                            </div>
                        </div>
                        <div class="contact-form__field-group contact-form__field--textarea">
                            <textarea id="opinion" name="opinion" class="contact-form__textarea"
                                placeholder="Ваше предложение или вопрос (необязательно)"
                                v-model="formData.opinion"></textarea>
                            <!-- <img class="contact-form__icon contact-form__icon--desc" src="../../assets/i4.svg"
                                alt="image" /> -->
                        </div>
                    </div>
                    <div class="contact-form__foot">
                        <div class="contact-form__field contact-form__field--button">
                            <button type="submit" class="contact-form__submit-btn social-join__btn box-shadow__btn">
                                Отправить <img :src="sendIcon" alt="icon" class="contact-form__submit-icon" />
                            </button>
                        </div>
                        <p class="contact-form__agreement">
                            Нажимая «Отправить», вы автоматически соглашаетесь
                            <a href="#">с политикой обработки персональных данных</a>
                        </p>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            formData: {
                name: '',
                phone: '',
                email: '',
                opinion: ''
            }
        }

            ;
    }

    ,
    methods: {
        submitForm() {
            // Логика отправки формы
            console.log('Form submitted:', this.formData);
        }
    }
};
</script>

<style scoped></style>