<template>
  <div
    class="p-4 bg-gray-600 rounded-md ring-1 ring-gray-200"
  >
    <div class="flex items-center space-x-1 text-gray-100">
      <span class="flex-grow space-x-2 text-left truncate hover:underline">
        {{ name }}
      </span>

      <div class="flex items-center space-x-1">
        <div class="flex items-center space-x-1">
          <span>{{ stars }}</span>
          <icon name="star-filled" class="w-6 h-6 text-yellow-600" />
        </div>

        <icon
          v-if="getLanguageIcon"
          :name="getLanguageIcon"
          :title="language"
          class="w-5 h-5"
        />
      </div>
    </div>

    <p class="text-gray-100 text-left line-clamp-2">
      {{ description }}
    </p>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
    },
    language: {
      type: String,
      required: false,
      default: () => null,
    },
    stars: {
      type: [String, Number],
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
  },
  computed: {
    getLanguageIcon() {
      const icons = {
        "C#" :"c",
      }

      return icons[this.language] || false
    },
  },
}
</script>
