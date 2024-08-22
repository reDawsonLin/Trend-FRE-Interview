<script setup>
defineProps({ name: String });
</script>

<template>
  <div class="box_icon">
    <svg
      v-if="name === 'arrow_left'"
      width="100%"
      height="100%"
      viewBox="0 0 13 9"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        d="M0.646446 4.14645C0.451184 4.34171 0.451184 4.65829 0.646446 4.85355L3.82843 8.03553C4.02369 8.2308 4.34027 8.2308 4.53553 8.03553C4.7308 7.84027 4.7308 7.52369 4.53553 7.32843L1.70711 4.5L4.53553 1.67157C4.7308 1.47631 4.7308 1.15973 4.53553 0.964466C4.34027 0.769204 4.02369 0.769204 3.82843 0.964466L0.646446 4.14645ZM13 4L1 4V5L13 5V4Z"
        fill="currentColor"
      />
    </svg>

    <svg
      v-else-if="name === 'facebook'"
      width="100%"
      height="100%"
      viewBox="0 0 16 16"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <g clip-path="url(#clip0_5248_646)">
        <path
          d="M10.6647 2.65667H12.1254V0.112667C11.8734 0.078 11.0067 0 9.99736 0C7.89136 0 6.44869 1.32467 6.44869 3.75933V6H4.12469V8.844H6.44869V16H9.29803V8.84467H11.528L11.882 6.00067H9.29736V4.04133C9.29803 3.21933 9.51936 2.65667 10.6647 2.65667Z"
          fill="currentColor"
        />
      </g>
      <defs>
        <clipPath id="clip0_5248_646">
          <rect width="16" height="16" fill="none" />
        </clipPath>
      </defs>
    </svg>

    <svg
      v-else-if="name === 'google'"
      width="100%"
      height="100%"
      viewBox="0 0 16 16"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        d="M8 6.4V9.6H12.5264C11.8656 11.4624 10.0864 12.8 8 12.8C5.3536 12.8 3.2 10.6464 3.2 8C3.2 5.3536 5.3536 3.2 8 3.2C9.1472 3.2 10.2512 3.6112 11.1088 4.3584L13.2112 1.9456C11.7712 0.6912 9.9216 0 8 0C3.5888 0 0 3.5888 0 8C0 12.4112 3.5888 16 8 16C12.4112 16 16 12.4112 16 8V6.4H8Z"
        fill="currentColor"
      />
    </svg>

    <svg
      v-else-if="name === 'warn'"
      width="100%"
      height="100%"
      viewBox="0 0 21 20"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        d="M10.5 0C4.9775 0 0.5 4.4775 0.5 10C0.5 15.5225 4.9775 20 10.5 20C16.0225 20 20.5 15.5225 20.5 10C20.5 4.4775 16.0225 0 10.5 0ZM11.75 16.25H9.25V13.75H11.75V16.25ZM11.75 12.5H9.25V5H11.75V12.5Z"
        fill="currentColor"
      />
    </svg>

    <svg
      v-else-if="name === 'eye'"
      width="100%"
      height="100%"
      viewBox="0 0 19 19"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        d="M18.8792 9.13046C18.7095 8.89826 14.6652 3.44507 9.49991 3.44507C4.33461 3.44507 0.290122 8.89827 0.120569 9.13024C-0.0401895 9.35052 -0.0401895 9.64929 0.120569 9.86957C0.290122 10.1018 4.33461 15.555 9.49991 15.555C14.6652 15.555 18.7095 10.1017 18.8792 9.86975C19.0402 9.64951 19.0402 9.35052 18.8792 9.13046ZM9.49991 14.3022C5.69511 14.3022 2.39976 10.6828 1.42426 9.49959C2.39849 8.31531 5.68695 4.69781 9.49991 4.69781C13.3045 4.69781 16.5996 8.31657 17.5756 9.50044C16.6013 10.6847 13.3129 14.3022 9.49991 14.3022Z"
        fill="currentColor"
      />
      <path
        d="M9.4999 5.7417C7.42763 5.7417 5.74164 7.42769 5.74164 9.49996C5.74164 11.5722 7.42763 13.2582 9.4999 13.2582C11.5722 13.2582 13.2582 11.5722 13.2582 9.49996C13.2582 7.42769 11.5722 5.7417 9.4999 5.7417ZM9.4999 12.0054C8.11831 12.0054 6.99442 10.8815 6.99442 9.49996C6.99442 8.11841 8.11835 6.99448 9.4999 6.99448C10.8814 6.99448 12.0054 8.11841 12.0054 9.49996C12.0054 10.8815 10.8815 12.0054 9.4999 12.0054Z"
        fill="currentColor"
      />
    </svg>

    <svg
      v-else-if="name === 'check'"
      width="100%"
      height="100%"
      viewBox="0 0 11 11"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <circle cx="5.5" cy="5.5" r="5.5" fill="currentColor" />
      <path
        d="M3 6.18182L5.08333 8L8 4"
        stroke="white"
        stroke-linecap="round"
        stroke-linejoin="round"
      />
    </svg>

    <svg
      v-else-if="name === 'checkPure'"
      width="100%"
      height="100%"
      viewBox="0 0 11 9"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        d="M9.5 0L11 1.25L4.5 8.75L0 4.25L1.375 2.875L4.375 5.875L9.5 0Z"
        fill="currentColor"
      />
    </svg>
  </div>
</template>

<style scoped>
.box_icon {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
