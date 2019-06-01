<script>
import Vue from 'vue';

export default {
  data: () => ({
    scopeData: {
      user: {
        firstName: '',
        lastName: ''
      }
    }
  }),

  watch: {
    'scopeData.user': {
      handler (val) {
        this.$emit('input:user', val);
      },
      deep: true
    }
  },

  methods: {
    updateUser (data) {
      const updated = Object.assign({}, this.scopeData.user, data);
      Vue.set(this.scopeData, 'user', updated);
    },
    insertBob () {
      this.updateUser({
        firstName: 'Bob',
        lastName: 'Marley'
      });
    }
  },

  render () {
    return this.$scopedSlots.default({
      // DATA
      ...this.scopeData,

      // ACTIONS
      updateUser: this.updateUser,
      insertBob: this.insertBob
    });
  }
};
</script>
