<script setup lang="ts">
// Xin chao ban minh ten la Thanh
  function recoverFromError(error: any) {
    error.value = null;
  }
</script>

<template>
  <NuxtLayout>
    <NuxtErrorBoundary>
      <!-- error boundary: When an error occurs, the internal component is re-rendered / receives the error thrown
       and renders the error slot if there is an error value, and renders the default slot if there is no error value. -->
       <NuxtLoadingIndicator color="#1a8bcd"/>
       <NuxtPage />

       <template #error="{ error }">
        <div>
          <h1>{{ error.value.statusCode }}</h1>
          <p>{{ error.value.statusMessage }}</p>
          <button 
            type="button"
            @click="recoverFromError(error)"
          >
            Revert
          </button>
        </div>
      </template>
    </NuxtErrorBoundary>
  </NuxtLayout>
</template>
