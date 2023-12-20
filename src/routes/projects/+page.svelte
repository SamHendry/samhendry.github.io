<script>
    import Logo from '$lib/Logo.svelte';
    import Footer from '../../lib/Footer.svelte';
    import { projects } from '$lib/pages.js'; // no +page.server.js bc using SSG?
</script>

<nav>
    <a id=hendry-logo href='/'>
        <Logo/>
    </a>
    <i id="left-arrow" class="ph ph-arrow-circle-left"></i>
    <i id="right-arrow" class="ph ph-arrow-circle-right"></i>
</nav>

<div id="scrolling-section">
    <h3>Projects</h3>
    {#each projects as project}
        <article id={project.name}>
            <div id="text">
                <h4>{project.name}</h4>
                <p>{project.description}</p>
            </div>
            <i class="ph ph-arrow-circle-up-right"></i>
        </article>
    {/each}
</div>

<Footer --position='block'/>

<style>
    nav {
        position: fixed;
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        width: 9%;
        height: 100%;
        top: 0;
    }

    #hendry-logo {
        cursor: pointer;
        margin-top: 20%;
        margin-bottom: 20%;
    }

    nav i {
        font-size: 40px;
        margin-bottom: 10%;
        color: #dadbde;
    }

    nav i.active {
        cursor: pointer;
        color: #343330;
    }

    /* main section */
    #scrolling-section {
        background: white;
        border: solid 1px black;
        border-radius: 20px;
        margin-left: 9%;
        margin-right: 3%;
        width: auto;
        margin-top: 70px;

        padding-bottom: 50px;
    }

    /* injected content */
    #scrolling-section h3 {
        margin-top: 0;
        margin-bottom: 15px;
        padding-top: 25px;
        padding-bottom: 25px;
        padding-left: 50px;
        border-bottom: dashed 1px black;
    }

    #scrolling-section > :is(p, h4, ul, ol) {
        margin-left: 50px;
        margin-right: 50px;
    }

    #scrolling-section > h4 {
        margin-bottom: 0px;
    }

    #scrolling-section > p {
        margin-top: 5px;
        margin-bottom: 5px;
    }

    article h4 {
        margin-top: 15px;
        margin-bottom: 0;
    }

    article { 
        display: flex; 
        padding: 0 50px 0 50px;
    }

    article i { padding-top: 20px; }

    article #text p {
        margin-top: 10px;
        margin-bottom: 15px;
    }

    article:hover {
        background: #f6f7f8;
        cursor: pointer;
    }


    @media screen and (max-width: 768px) {
        nav {
            position: static;
            flex-direction: row;
            width: 100%;
            height: 70px;
            
            
        }
        nav i {
            margin-bottom: 0;
            margin-left: 20px;
        }
        
        #hendry-logo {
            margin-top: 0;
            margin-bottom: 0;
            margin-left: 5%;
            margin-right: 0;

            width: 30px;
        }

        #scrolling-section {
            margin-top: 0;
            margin-left: 5%;
            margin-right: 5%;
        }
    }
</style>