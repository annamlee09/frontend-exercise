<template>
    <transition name="modal-transition">
        <div class="modal-container">
            <div class="modal">
                <header class="modal-header">
                    <h2>Quiz Summary</h2>
                    <button class="btn-close" @click="$emit('close')">
                        x
                    </button>
                </header>
                <div class="modal-body">
                    <div v-for="(question, index) in questions">
                        <h2>{{ question.text }}</h2>
                        <h3>{{ responses[index] }}</h3>
                    </div>
                </div>
                <footer class="modal-footer">
                    <button class="btn-restart" @click="$emit('restart')">
                        Restart
                    </button>
                </footer>
            </div>
        </div>
    </transition>
</template>

<script>

export default {
    name: 'summary-modal',
    props: ['questions', 'responses']
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
    padding: 10px;
    background: #FFFFFF;
    box-shadow: 2px 2px 20px 1px;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
    border-radius: 20px;
    justify-content: center;
    align-items: center
}

.modal-header,
.modal-footer {
    padding: 15px;
    display: flex;
}

.modal-header {
    position: relative;
    border-bottom: 1px solid #eeeeee;
    color: #42b883;
}

.modal-footer {
    flex-direction: column;
    align-self: stretch;
}

.modal-body {
    position: relative;
    padding: 0 10px;
}

.btn-close {
    position: absolute;
    bottom: 50%;
    left: 160%;
    border: none;
    font-size: 25px;
    cursor: pointer;
    font-weight: bold;
    color: #42b883;
    background: transparent;
    border-radius: 50%;
    width: 50px;
    height: 50px;

    &:hover {
        background-color: rgba(0, 0, 0, 0.05);
    }
}


.btn-restart {
    border: none;
    background-color: #42b883;
    color: #ffffff;
    border-radius: 20px;
    border-color: #42b883;
    padding: 10px 20px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    transition-duration: 0.4s;
    cursor: pointer;
    width: 100%;

    &:hover {
        background-color: rgba(66, 184, 131, 0.7);
    }
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