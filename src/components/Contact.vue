<template>
  <div class="parallax">
    <div class="container">
      <div class="contact">
        <h2 id="contact" class="contact__title">Contact Me</h2>
        <section class="contact-form">
          <div class="contact-text">
            <p class="contact-text__description">
              If you have any questions, please feel free to fill out the contact form or write me directly to my email. I will be happy to get in touch with you.
            </p>

            <div class="item-icon">
              <Icon icon="bi:pin-map-fill" width="32" height="32" />
              <p>Medellín, Colombia</p>
            </div>
            <div class="item-icon">
              <Icon icon="mdi:email-outline" width="32" height="32" />
              <p>kathegomv@gmail.com</p>
            </div>
          </div>
          <div class="form">
            <el-form
              ref="formRef"
              style="max-width: 500px"
              :model="infoForm"
              :rules="rules"
              class="demo-ruleForm"
              label-width="auto"
              size="large"
            >
              <el-form-item label="Email" prop="email">
                <el-input v-model="infoForm.email" name="email" />
              </el-form-item>
              <el-form-item label="Subject" prop="subject">
                <el-input v-model="infoForm.subject" name="subject" />
              </el-form-item>
              <el-form-item label="Message" prop="message">
                <el-input
                  v-model="infoForm.message"
                  type="textarea"
                  maxlength="100"
                  name="message"
                />
              </el-form-item>
              <el-form-item>
                <el-button  @click="submitForm()">
                  Submit
                </el-button>
              </el-form-item>
            </el-form>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>
  
  <script setup>
//----------IMPORTS----------//
import { Icon } from "@iconify/vue";
import { ref, reactive } from "vue";
import { ElNotification } from "element-plus";

//----------VARIABLES----------//
const formRef = ref(null);
const infoForm = reactive({
  email: "",
  subject: "",
  message: "",
});

//----------METHODS----------//
const submitForm = async () => {
  formRef.value?.validate(async (valid) => {
    if (!valid) {
      console.log("entreee");
      return;
    }

    const formData = new FormData();
    formData.append("email", infoForm.email);
    formData.append("subject", infoForm.subject);
    formData.append("message", infoForm.message);
    formData.append("_captcha", "true");
    formData.append("_template", "box");
    formData.append(
      "_autoresponse",
      "Thanks for contacting me, I will answer you soon 😊."
    );
    console.log("2");
    try {
      const response = await fetch(
        "https://formsubmit.co/ajax/kathegomv@gmail.com",
        {
          method: "POST",
          headers: {
            Accept: "application/json",
          },
          body: formData,
        }
      );

      if (response.ok) {
        ElNotification({
          title: "Message sent successfully",
          message: "Thanks for contacting me, I will answer you soon 😊.",
          type: "success",
        });

        // Limpiar formulario
        infoForm.email = "";
        infoForm.subject = "";
        infoForm.message = "";
      } else {
        ElNotification({
          title: "Error",
          message: "The message could not be sent. Please try again.",
          type: "error",
        });
      }
    } catch (error) {
      console.error(error);
      ElNotification({
        title: "Error",
        message: "An error occurred while sending your message",
        type: "error",
      });
    }
  });
};

const rules = reactive({
  email: [
    {
      type: "email",
      required: true,
      message: "Please input correct email address",
      trigger: "blur",
    },
  ],
  subject: [
    { required: true, message: "Please input subject", trigger: "blur" },
  ],
  message: [
    { required: true, message: "Please input message", trigger: "blur" },
  ],
});
</script>
  
  <style lang="scss"scoped>
.container {
  background-color: $color-white;
  width: 80%;
  height: auto;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 1400px;
}

.contact {
  background-color: $color-white;
  text-align: center;
  margin: 0px auto;
  height: 800px;
  width: 100%;
  border: 20px solid $color-white;
  border-radius: 10px;
  padding: 10px;
  &__title {
    @include general-title(5.0em);
    margin: 0;
  }
}

.contact-form {
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  justify-items: center;
  padding: 20px 10px;
}

.contact-text {
  display: flex;
  flex-direction: column;
  &__description {
    text-align: left;
    width: 450px;
    font-size: 1.2em;
  }
}
.item-icon {
  display: flex;
  align-items: center;
  p {
    margin: 10px 20px;
    font-size: 1.2em;
  }
}

.form {
  width: 100%;
}

.parallax {
  position: relative;
  min-height: 800px;
  overflow: hidden;
}

.parallax::before {
  content: "";
  position: absolute;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url("../../public/landscape.jpg");
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 0.2;
  z-index: 1;
  pointer-events: none;
}

:deep(.el-form-item__label) {
  --el-form-label-font-size: 1.2em;
  font-size: 1.2em;
}

:deep(.el-input__wrapper) {
  box-shadow: $color-app-gray !important;
}

:deep(.el-input__wrapper.is-focus) {
  --el-input-focus-border-color: $color-app-gray;
  box-shadow: 0 0 0 2px rgba(191, 191, 191);
}

:deep(.el-input__inner) {
  font-family: $font-family-text;
}

:deep(.el-textarea__inner) {
  max-height: 200px;
  &:focus {
    --el-input-focus-border-color: $color-app-gray;
    box-shadow: 0 0 0 2px rgba(191, 191, 191);
  }
}

:deep(.el-form-item__content) {
  display: flex;
  justify-content: center;
}

:deep(.el-button--large) {
  background-color: $color-title;
  color: $color-white;
  --el-font-size-base: $font-family-text;
  font-family: $font-family-text;
  &:hover {
    background-color: lighten($color-title, 5%);
    color: $color-white;
    border-color: $color-title;
  }
}
</style>