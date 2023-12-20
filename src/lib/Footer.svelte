<footer>
    <div id="copyright">
        <i class="ph ph-copyright"></i>
        <p class="small">Designed and developed by Samuel Hendry Eaton</p>
    </div>
    <div id="footer-right">
        <a href="mailto:samuel@darryl.net">
            <i class="ph ph-envelope"></i>
        </a>
        <a href="https://github.com/SamHendry">
            <i class="ph ph-github-logo"></i>
        </a>
        <a href="https://www.linkedin.com/in/samuelhendryeaton/">
            <i class="ph ph-linkedin-logo"></i>
        </a>
    </div>
</footer>

<style>
    footer {
    position: var(--position);
    bottom: 0;
    width: 100%;
    height: 100px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    }

    /* footer right box */
    #footer-right {
        display: flex;
        justify-content: center;
        align-items: center;
        margin-right: 3%;
        background-color: white;
        height: 50px;
        padding-left: 30px;
        padding-right: 30px;
        border-radius: 20px;
        border: 1px solid black;
        box-shadow: 2px 2px 0 0 rgb(0 0 0 / 15%);

        transition: all 0.1s ease;
    }

    #footer-right:hover {
        transform: translate(-1px, -1px);
        box-shadow: 3px 3px 0 0 rgb(0 0 0 / 20%);
    }

    #footer-right a {
        margin-left: 18px;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    #footer-right a:first-child {
        margin-left: 0;
    }

    #copyright {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-left: 3%;
    }

    #copyright i {
        padding-right: 10px;
        font-size: 18px;
    }
</style>