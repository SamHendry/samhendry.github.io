<script>
    export let text;
    export let icon;
    export let href;
</script>

<a {href}>
    <button>
        <i class={icon}></i>
        <h4>{text}</h4>
    </button>
</a>

<style>
    button {
        width: 246px;
        height: 76px;
        background-color: white;
        border: 1px solid #343330;
        border-radius: 20px;
        display: flex;
        justify-content: center;
        align-items: center;
        box-shadow: 2px 2px 0 0 rgb(0 0 0 / 15%);

        transition: all 0.1s ease;
    }

    i {
        margin-right: 20px;
    }

    h4 {
        font-weight: 400;
    }

    button:hover {
        transform: translate(-1px, -1px);
        box-shadow: 3px 3px 0 0 rgb(0 0 0 / 20%);
        cursor: pointer;
    }

    button:active {
        transform: translate(1px, 1px);
        box-shadow: 0px 0px 0 0 rgb(0 0 0 / 20%);
        cursor: pointer;
    }

    @media screen and (max-width: 768px) {
        button {
            margin-bottom: 20px;
            width: 300px;
        }
    }
</style>