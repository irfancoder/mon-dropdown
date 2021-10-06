<template>
    <div class="mon-dropdown">
        <div>
            <transition
                v-if="!persistent"
                :enter-active-class="enterActiveClass"
                :enter-class="enterClass"
                :enter-to-class="enterToClass"
                :leave-active-class="leaveActiveClass"
                :leave-class="leaveClass"
                :leave-to-class="leaveToClass"
            >
                <div v-if="show" :class="`${contentClass} mon-dropdown-anchor-${anchor} ${dropdownDirection}`">
                    <slot name="content" :close="closeDropdown" :toggle="toggleDropdown"> </slot>
                </div>
            </transition>
            <transition
                v-else
                :enter-active-class="enterActiveClass"
                :enter-class="enterClass"
                :enter-to-class="enterToClass"
                :leave-active-class="leaveActiveClass"
                :leave-class="leaveClass"
                :leave-to-class="leaveToClass"
            >
                <div v-show="show" :class="`${contentClass} mon-dropdown-anchor-${anchor} ${dropdownDirection}`">
                    <slot name="content" :close="closeDropdown" :toggle="toggleDropdown"> </slot>
                </div>
            </transition>

            <button v-if="!$scopedSlots.trigger" @click="toggleDropdown" aria-haspopup="true" aria-expanded="true" :class="labelClass" @focusout="!disableClickAway ? closeDropdown() : null">
                {{ label }}
            </button>
            <div v-else tabindex="0" @focusout="!disableClickAway ? closeDropdown() : null">
                <slot name="trigger" :open="openDropdown" :close="closeDropdown" :toggle="toggleDropdown"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default /*#__PURE__*/ {
    name: 'MonDropdown', // vue component name
    props: {
        label: { type: String, required: false },
        labelClass: { type: String, required: false },
        contentClass: { type: String, required: false, default: 'mon-dropdown-content' },
        enterActiveClass: { type: String, required: false, default: 'mon-dropdown-enter-active' },
        enterClass: { type: String, required: false, default: 'mon-dropdown-enter' },
        enterToClass: { type: String, required: false, default: 'mon-dropdown-enter-to' },
        leaveActiveClass: { type: String, required: false, default: 'mon-dropdown-leave-active' },
        leaveClass: { type: String, required: false, default: 'mon-dropdown-leave' },
        leaveToClass: { type: String, required: false, default: 'mon-dropdown-leave-to' },
        anchor: { type: String, required: false, default: 'left' },
        dropUp: { type: Boolean, required: false, default: false },
        persistent: { type: Boolean, required: false, default: false },
        openOnMount: { type: Boolean, required: false, default: false },
        disableClickAway: { type: Boolean, required: false, default: false },
        disableEsc: { type: Boolean, required: false, default: false }
    },
    data() {
        return {
            show: false
        }
    },

    mounted() {
        if (this.openOnMount) this.openDropdown()
        if (!this.disableEsc) document.addEventListener('keydown', this.bindEscKey)
    },

    computed: {
        dropdownDirection() {
            return this.dropUp ? 'mon-drop-up' : 'mon-drop-down'
        }
    },

    beforeDestroy() {
        if (!this.disableEsc) document.removeEventListener('keydown', this.bindEscKey)
    },
    methods: {
        toggleDropdown() {
            if (this.show) this.closeDropdown()
            else this.openDropdown()
        },

        openDropdown() {
            this.$emit('before-open')
            this.show = true
            this.$emit('after-open')
        },
        closeDropdown() {
            this.$emit('before-close')
            this.show = false
            this.$emit('after-close')
        },

        bindEscKey: function(event) {
            if (this.show === true && event.keyCode === 27) this.closeDropdown()
        }
    }
}
</script>

<style scoped>
.mon-dropdown {
    position: relative;
    display: inline-block;
}

.mon-dropdown-content {
    border-radius: 0.375rem;
    box-shadow: 0 3px 10px rgb(0 0 0 / 0.2);
    overflow: hidden;
    border-width: 1px;
    z-index: 20;
    background: white;
}

/* ANCHORS */
.mon-dropdown-anchor-left {
    position: absolute;
    left: 0;
}

.mon-dropdown-anchor-right {
    position: absolute;
    right: 0;
}

/* DIRECTION */
.mon-drop-up {
    bottom: 100%;
    margin-bottom: 4px;
}

.mon-drop-down {
    top: 100%;
    margin-top: 4px;
}

/* TRANSITIONS */
.mon-dropdown-enter-active {
    transition: all;
    transition-timing-function: cubic-bezier(0, 0, 0.2, 1);
    transition-duration: 100ms;
}

.mon-dropdown-enter {
    transform: scale(0.95);
    opacity: 1;
}

.mon-dropdown-enter-to {
    transform: scale(1);
    opacity: 1;
}

.mon-dropdown-leave-active {
    transition: all;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
    transition-duration: 75ms;
}

.mon-dropdown-leave {
    transform: scale(1);
    opacity: 1;
}

.mon-dropdown-leave-to {
    transform: scale(0.95);
    opacity: 0;
}
</style>
