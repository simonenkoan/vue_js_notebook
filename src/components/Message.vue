<template>
    <div class="message">
        <p> Message Component - {{message}}</p>
    </div>
</template>


<script>
export default {
    props: {
        message: {
            type: String,
            required: true,
            default: "Default Message"
        }
    }
}
</script>

<style lang="scss" scoped>
.message{
    text-align: center;
}
p {
    color: red;
}

</style>