<template>
    <input
      name="search"
      id="search"
      autocomplete="off"
      :class="{ dark}"
      :value="value"
      @input="handleChange"
    />
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
    dark: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>

  input
  {
    height: 30px;
    border: 0;
    color: white;
    text-align: center;
    background: none;
    border-bottom: 1px solid white;
    font-weight: 300;
    font-size: 18px;
    transition: box-shadow .3s ease-in-out;
    margin-top: 30px;

    @media (min-width: 1024px)
    {
      font-weight: 400;
    }

    &:focus
    {
      outline: none;
      box-shadow: 0 10px 20px -8px rgba(255,255,255, .3);
    }
    &.dark
    {
      color: #1e3d4a;
      border-bottom-color: #1e3d4a;
      &:focus
      {
        outline: none;
        box-shadow: 0 10px 20px -8px rgba(#1e3d4a, .3);
      }
    }
  }

</style>
