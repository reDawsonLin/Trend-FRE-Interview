<script setup>
import ButtonCTA from "./components/ButtonCTA.vue";
import Icons from "./components/Icons.vue";
import { Form, Field } from "vee-validate";
import * as Yup from "yup";
import { ref } from "vue";

const data_signUp = ref({
  firstName: "",
  lastName: "",
  email: "",
  password: "",
  checkPolicy: false,
});
const showPassword = ref(false);
const checkPasswordLength = ref(false);
const checkPasswordNumber = ref(false);
const checkPassword = (event) => {
  const value = event.target.value;
  value.length >= 8
    ? (checkPasswordLength.value = true)
    : (checkPasswordLength.value = false);

  const regex = /^(?=.*\d).+$/;
  regex.test(value)
    ? (checkPasswordNumber.value = true)
    : (checkPasswordNumber.value = false);
};

// form rules -------
const schema = Yup.object().shape({
  firstName: Yup.string().required("Please enter your first name"),
  lastName: Yup.string().required("Please enter your last name"),
  email: Yup.string()
    .email("Please enter a valid email")
    .required("Please enter your email"),
  password: Yup.mixed()
    .test(
      "min length",
      "Please enter ata least 8 characters",
      (value) => value.length >= 8
    )
    .test("one number", "Please enter at least one number", (value) => {
      const regex = /^(?=.*\d).+$/;
      checkPasswordNumber.value = regex.test(value);
      return regex.test(value);
    }),
});

// submit -------
const error_formSubmitted = ref(false);
const onSubmit = async (value) => {
  if (!data_signUp.value.policyCheck) {
    alert("Please check the policy");
    return;
  }

  console.log("value :>> ", value);
  error_formSubmitted.value = false;
  alert("create account success!");
};

// onInvalid submit -------
const onInvalidSubmit = (error) => {
  error_formSubmitted.value = true;
  console.log("error :>> ", error);
};
</script>

<template>
  <div class="container">
    <nav class="">
      <div class="box_nav">
        <Icons name="arrow_left" class="icon_arrow" />
        <p class="">Back</p>
      </div>
    </nav>

    <main class="">
      <header>
        <hgroup>
          <p>Start from free</p>
          <h1>Create an account</h1>
        </hgroup>

        <div v-if="false" class="callout_error">
          <Icons name="warn" />
          <p class="">Please complete all the required fields to proceed.</p>
        </div>

        <div class="box_signIn">
          <ButtonCTA type="button" buttonStyle="line" iconName="google">
            <p>Sign up with Google</p>
          </ButtonCTA>
          <ButtonCTA type="button" buttonStyle="line" iconName="facebook">
            <p>Sign up with Facebook</p>
          </ButtonCTA>
        </div>

        <p class="divider">Or use your email for registration</p>
      </header>

      <Form
        id="formLogin"
        name="formLogin"
        class="form_login"
        @submit="onSubmit"
        @invalid-submit="onInvalidSubmit"
        :validation-schema="schema"
        v-slot="{ errors }"
      >
        <div class="row">
          <label
            class="box_input"
            :class="{
              label_upper: errors.firstName || data_signUp.firstName,
              error: errors?.firstName,
            }"
            data-name="First Name"
          >
            <Field
              v-model="data_signUp.firstName"
              name="firstName"
              type="text"
              :validate-on-change="false"
              :validate-on-blur="false"
              :validate-on-model-update="false"
            />
          </label>

          <label
            class="box_input"
            :class="{
              label_upper: errors.lastName || data_signUp.lastName,
              error: errors?.lastName,
            }"
            data-name="Last Name"
          >
            <Field
              v-model="data_signUp.lastName"
              name="lastName"
              type="text"
              :validate-on-change="false"
              :validate-on-blur="false"
              :validate-on-model-update="false"
            />
          </label>
        </div>

        <label
          class="box_input"
          :class="{
            label_upper: errors.email || data_signUp.email,
            error: errors?.email,
          }"
          data-name="E-mail"
        >
          <Field
            v-model="data_signUp.email"
            name="email"
            type="text"
            :validate-on-change="false"
            :validate-on-blur="false"
            :validate-on-model-update="false"
          />
        </label>

        <div class="wrapper_password">
          <label
            class="box_input"
            :class="{
              label_upper: errors.password || data_signUp.password,
              error: errors?.password,
            }"
            data-name="Password"
          >
            <Field
              v-model="data_signUp.password"
              name="password"
              :type="showPassword ? 'text' : 'password'"
              :validate-on-change="false"
              :validate-on-blur="false"
              :validate-on-model-update="false"
              @input="checkPassword"
            />

            <Icons
              name="eye"
              class="eye"
              :class="{ open: showPassword }"
              @click="showPassword = !showPassword"
            />
          </label>

          <div class="box_remind">
            <p class="checkpoint">
              <Icons name="check" :class="{ c_success: checkPasswordLength }" />
              8 characters min.
            </p>
            <p class="checkpoint">
              <Icons name="check" :class="{ c_success: checkPasswordNumber }" />
              One number
            </p>
          </div>
        </div>
      </Form>

      <div class="box_cta">
        <div class="box_checkbox">
          <label class="checkbox">
            <input
              type="checkbox"
              name="policy check"
              v-model="data_signUp.policyCheck"
            />
            <Icons v-show="data_signUp.policyCheck" name="checkPure" />
          </label>
          <p>
            By creating account, you agree to accept our Privacy Policy, Terms of Service
            and Notification settings.
          </p>
        </div>

        <ButtonCTA type="submit" class="btn_cta" form="formLogin">Create an Free Account! </ButtonCTA>

        <p class="member_current">
          Already have an account?
          <a href="">Log in</a>
        </p>
      </div>
    </main>
  </div>
</template>

<style scoped>
.container {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  width: 100%;
  max-width: 610px;
  padding: 1.5rem 0.5rem;
  margin: 0 auto;
  background-color: var(--white);
  border-radius: 0.25rem;
  font-size: 0.875rem;

  @media (min-width: 576px) {
    flex-grow: unset;
  }
}

nav {
  display: flex;
  padding: 0 1rem;

  .box_nav {
    display: flex;
    gap: 0.5rem;
    border-bottom: 2px solid transparent;
    transition: border-bottom-color 0.15s ease;
    cursor: pointer;

    .icon_arrow {
      width: 0.75rem;
    }

    &:hover {
      border-bottom-color: var(--primary);
    }
  }
}

main {
  align-self: center;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  max-width: 400px;
}

header {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

hgroup {
  > h1 {
    font-size: 1.875rem;
    font-weight: 700;
  }

  > p {
    font-size: 1.125rem;
    margin-bottom: 0.5rem;
  }
}

.callout_error {
  display: flex;
  gap: 0.75rem;
  padding: 1rem;
  font-size: 1rem;
  background-color: var(--bg-warning);
  border-radius: 0.25rem;
  border: 1px solid var(--warning);

  > .box_icon {
    width: 1rem;
  }
}

.box_signIn {
  display: flex;
  justify-content: space-between;
  gap: 1.25rem;
  flex-wrap: wrap;
  font-size: 13px;

  button {
    flex-grow: 1;

    > p {
      text-align: left;
    }
  }
}

.divider {
  position: relative;
  display: flex;
  align-items: center;
  gap: 1rem;

  &::after {
    content: "";
    flex-grow: 1;
    height: 1px;
    background-color: currentColor;
  }
}

/* -------- */
.form_login {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.row {
  display: flex;
  gap: 1.25rem;
  > * {
    flex-grow: 1;
  }
}

.box_input {
  position: relative;
  display: flex;
  border-radius: 0.25rem;

  &::after {
    content: attr(data-name);
    position: absolute;
    top: 1rem;
    left: 0.75rem;
    color: var(--neutral-400);
    transition: top 0.15s ease, font-size 0.15s ease;
  }

  &:has(input:active, input:focus),
  &.label_upper {
    &::after {
      top: 0.5rem;
      font-size: 0.625rem;
    }
  }

  &.error {
    border: 2px solid var(--warning);
  }

  > input {
    flex-grow: 1;
    background-color: var(--bg-primary);
    border-radius: 0.25rem;
  }

  .eye {
    position: absolute;
    top: 14.5px;
    right: 14.5px;
    width: 19px;
    color: var(--neutral-300);
    transition: color 0.15s ease;
    cursor: pointer;

    &.open {
      color: var(--primary);
    }
  }
}

.wrapper_password {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.box_remind {
  display: flex;
  gap: 0.875rem;
}

.checkpoint {
  display: flex;
  gap: 0.25rem;
  color: var(--neutral-300);

  > .box_icon {
    width: 0.75rem;
  }
}

/* ------- */
.box_cta {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.btn_cta {
  justify-content: center;
}

.box_checkbox {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 13px;
  color: var(--neutral-400);

  .checkbox {
    flex-shrink: 0;
    position: relative;
    width: 1.125rem;
    height: 1.125rem;
    border: 1px solid transparent;
    border-radius: 2px;
    background-color: var(--neutral-300);
    cursor: pointer;

    &:has(input:checked) {
      background-color: var(--white);
      border: 1px solid var(--primary);
    }

    > input {
      display: none;
    }

    > .box_icon {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 0.75rem;
      color: var(--primary);
    }
  }
}

.member_current {
  display: flex;
  justify-content: center;
  gap: 0.25rem;
  font-size: 13px;
  color: var(--neutral-400);

  > a {
    text-decoration: none;
    color: var(--primary);
    border-bottom: 2px solid transparent;
    transition: border-bottom-color 0.15s ease;

    &:hover {
      border-bottom-color: var(--primary);
    }
  }
}

</style>
