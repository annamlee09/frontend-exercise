<template>
    <transition name="modal-transition">
        <div class="modal-container">
            <div class="modal">
                <header class="modal-header" id="modalTitle">
                    <button class="btn-close" @click="$emit('close')">
                        x
                    </button>
                </header>
                <section class="modal-body" id="modalDescription">
                    <slot name="body">

                    </slot>
                </section>
                <footer class="modal-footer">
                    <button class="btn-green" @click="$emit('restart')">
                        Restart
                    </button>
                </footer>
            </div>
        </div>
    </transition>
</template>

<script>

export default {
    name: 'summary',
    props: ['responses']
}

</script>

<style>
.modal-container {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.3);
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal {
    background: #FFFFFF;
    box-shadow: 2px 2px 20px 1px;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
}

.modal-header,
.modal-footer {
    padding: 15px;
    display: flex;
}

.modal-header {
    position: relative;
    border-bottom: 1px solid #eeeeee;
    color: #4AAE9B;
    justify-content: space-between;
}

.modal-footer {
    border-top: 1px solid #eeeeee;
    flex-direction: column;
}

.modal-body {
    position: relative;
    padding: 20px 10px;
}

.btn-close {
    position: absolute;
    top: 0;
    right: 0;
    border: none;
    font-size: 20px;
    padding: 10px;
    cursor: pointer;
    font-weight: bold;
    color: #4AAE9B;
    background: transparent;
}

.btn-green {
    color: white;
    background: #4AAE9B;
    border: 1px solid #4AAE9B;
    border-radius: 2px;
}

.modal-transition-enter,
.modal-transition-leave-to {
    opacity: 0;
}

.modal-transition-enter-active,
.modal-transition-leave-active {
    transition: opacity .5s ease;
}
</style>