<script>
    import Button from '$lib/Button.svelte';
    import Logo from '$lib/Logo.svelte';
    import Footer from '$lib/Footer.svelte';
</script>

<main id=homepage>
    <div id="name-bio">
        <h1>
            Sam 
            <div id="hendry-logo-wrap">
                <Logo />
            </div>
            endry
        </h1>
        <p>A <strong>designer</strong> and <strong>software engineer</strong> at <br>the University of California, Berkeley</p>
    </div>

    <div id="buttons">
        <Button href='/projects' text="Projects" icon="ph ph-circuitry" />
        <Button href='/writing' text="Writing" icon="ph ph-note-pencil" />
        <Button href='/resume' text="Resume" icon="ph ph-user-circle" />
    </div>
</main>

<Footer --position='fixed'/>

<style>
    /* middle */
    main {
        position: fixed;
        width: 900px;
        height: 300px;
        top: 48%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    /* buttons */
    #buttons {
        display: flex;
        justify-content: space-evenly;
        align-items: center;;
    }

    /* hero */
    #name-bio {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    #name-bio p {
        padding-top: 16px;
        padding-bottom: 15px;
        padding-left: 35px;
        width: calc(50% - 15px);
        border-left: 1px dashed black;
    }

    #name-bio h1 {
        padding-right: 30px;
        padding-bottom: 15px;
        width: 50%;
        margin-bottom: 40px;
        display: flex;
        align-items: center;
        justify-content: flex-end;
    }

    /* change the svg margin */
    #hendry-logo-wrap {
        margin-right: 5px;
        margin-left: 15px;
        display: flex;
    }

    @media screen and (max-width: 768px) {
        main {
            width: 100%;
            height: auto;
            left: 0;
            /* top: 50%; */
            transform: translate(0, -50%);
        }

        #name-bio {
            flex-direction: column;
        }

        #name-bio p {
            border-left: none;
            padding: 0;
            text-align: center;
        }

        #name-bio h1 {
            padding: 0;
            justify-content: center;
            border-bottom: dashed 1px black;
            padding-bottom: 35px;
            margin-bottom: 10px;
        }
        
        #buttons {
            flex-direction: column;
            align-items: center;
            margin-top: 30px;
        }
    }
</style>