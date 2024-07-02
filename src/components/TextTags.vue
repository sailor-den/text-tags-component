<template>
  <div :class="['text-tags', alignmentClass]" ref="container">
    <div v-for="(tag, index) in tags" :key="index" class="text-tags__tag">
      <v-icon v-if="tag.icon">{{ tag.icon }}</v-icon>
      <span>{{ tag.text }}</span>
      <v-icon v-if="index < tags.length - 1" class="text-tags__separator">mdi-circle-small</v-icon>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TextTags',
  props: {
    tags: {
      type: Array,
      required: true
    },
    alignment: {
      type: String,
      default: 'left',
      validator: value => ['left', 'justify'].includes(value)
    }
  },
  computed: {
    alignmentClass() {
      return this.alignment === 'justify' ? 'text-tags--justify' : 'text-tags--left';
    }
  }
};
</script>

<style lang="scss">
.text-tags {
  display: flex;
  flex-wrap: nowrap;
  overflow: hidden;

  &--left {
    justify-content: flex-start;
  }

  &--justify {
    justify-content: space-between;
  }

  &__tag {
    display: flex;
    align-items: center;
    white-space: nowrap;

    &__separator {
      margin: 0 4px;
    }
  }
}
</style>
