<script>
    // @ts-nocheck

    import logo from "/src/routes/elements/principleairlogo.svg";
    import { quintOut } from "svelte/easing";
    import { fade, draw, fly, crossfade, blur } from "svelte/transition";
    import { lpath } from "./elements/logopath.js";
    // @ts-ignore
    import Navbar from "./template/nav.svelte";
    import Navphone from "./template/navphone.svelte";
    import Icon from "svelte-awesome/components/Icon.svelte";
    // @ts-ignore
    import emblaCarouselSvelte from "embla-carousel-svelte";
    // @ts-ignore
    import Autoplay from "embla-carousel-autoplay";

    let options = { loop: true };
    let plugins = [Autoplay({ delay: 1250, stopOnInteraction: false })];
    import instagram from "svelte-awesome/icons/instagram";
    import MediaQuery from "./MediaQuery.svelte";
    import { onMount } from "svelte";
    import Contact from "./template/contact.svelte";
    import Footer from "./template/footer.svelte";
    let ready = false;
    onMount(() => (ready = true));

    // @ts-ignore
    import IntersectionObserver from "svelte-intersection-observer";
    /**
     * @type {any}
     */
    let elem1;
    let elem2;
    let elem3;
    let elem4;
</script>

<svelte:head>
    <title>Principle Air Systems</title>
    <meta name="title" content="Principle Air Systems" />
    <meta
        name="description"
        content="HVAC/R company serving the GTA with over 15 years of experience. We proudly serve the residential, commercial and industrial sectors."
    />
    <meta
        name="keywords"
        content="HVAC/R, building automation, commercial, industrial, residential, experienced"
    />
    <meta name="robots" content="index, follow" />
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta name="language" content="English" />
    <meta name="author" content="Pavithran Chelliahpillai" />
    <script type="application/ld+json">
        {
          "@context" : "https://schema.org",
          "@type" : "WebSite",
          "name" : "Principle Air Systems Inc",
          "url" : "https://principleair.com"
        }
    </script>
</svelte:head>

<MediaQuery query="(max-width: 1280px)" let:matches>
    {#if matches}
        <style>
            #offer2 {
                margin-left: 2vw !important;
            }
            .dispapp p {
                font-size: 2vw !important;
            }
            .dispapp h1 {
                font-size: 3vw !important;
            }
            h1 {
                font-size: 5vh !important;
            }
            #mimg {
                display: flex;
                align-items: center;
            }
            #types {
                flex-direction: column !important;
                height: auto;
                height: 0 !important;
            }
            #residential {
                height: 50vh;
            }
            #residential h1 {
                padding-top: 2vh;
                font-size: 4vh !important;
            }
            #residential p {
                font-size: 2vh !important;
            }
            #commercial {
                height: 50vh;
            }
            #commercial h1 {
                padding-top: 2vh;
                font-size: 4vh !important;
            }
            #commercial p {
                font-size: 2vh !important;
            }
            #industrial {
                height: 50vh !important;
            }
            #industrial h1 {
                padding-top: 2vh;
                font-size: 4vh !important;
            }
            #industrial p {
                font-size: 2vh !important;
            }
            .embla__container {
                display: grid;
                grid-auto-flow: column;
                grid-auto-columns: 33% !important;
            }
            #offers {
                flex-direction: column;
            }
            #free {
                font-size: 34.5vw !important;
            }
            #freeout2 {
                font-size: 34.5vw !important;
                -webkit-text-stroke: 0.7vw !important;
            }
            p {
                font-size: 3vh !important;
                padding-bottom: 1vh;
            }
            #phone {
                display: flex !important;
            }
            #phonebye {
                display: none !important;
            }
            #phone h1 {
                font-size: 3vh !important;
            }
            #widen {
                width: 100% !important;
            }
            .navphone {
                display: flex !important;
            }
            body {
                overflow-x: hidden !important;
            }
        </style>
    {/if}
</MediaQuery>

<body>
    <div id="phonebye" style="position: fixed; z-index: 5;">
        <Navbar></Navbar>
    </div>
    <div id="phone" style="position: fixed; z-index: 5;">
        <Navphone></Navphone>
    </div>
    <section class="bigfront">
        {#if ready}
            <video
                in:fade={{ delay: 20, duration: 2500 }}
                id="introvid"
                muted
                autoplay
                loop
                playsinline
                disablepictureinpicture
            >
                <source src="/bgvid.mp4" type="video/mp4" />
                <source src="/bgvid.mkv" type="video/mkv" />
                <source src="/bgvid.webm" type="video/webm" />
            </video>
            <!-- svelte-ignore a11y-missing-attribute -->
            <!-- <iframe id="introvid" height="5000"
                src="https://www.youtube.com/embed/rvD2TjA4u4o?autoplay=1&loop=1&mute=1" >
            </iframe> -->
        {/if}
        <div style="padding-top: 10vh;"></div>
        <div id="logo" style="position: relative; z-index: 7;">
            {#if ready}
                <svg viewBox="0 0 657 842">
                    <path
                        in:draw={{ duration: 5000 }}
                        style="stroke: white; stroke-width: 1.5;"
                        d={lpath}
                    />
                    <path
                        in:fade={{ delay: 2500, duration: 1500 }}
                        style="fill: white;"
                        d={lpath}
                    />
                </svg>
            {/if}
        </div>
    </section>
    <div class="hflex">
        <div class="box" style="border-left: 0;"></div>
        <div class="box"></div>
        <div class="box"></div>
    </div>
    <div class="flexbox">
        <div id="mimg">
            {#if ready}
                <video
                    in:blur={{ delay: 200, duration: 2500 }}
                    muted
                    autoplay
                    loop
                    playsinline
                    disablepictureinpicture
                >
                    <source src="\homevid.mp4" />
                </video>
            {/if}
        </div>
        <div id="mtext">
            <div
                style="width: 60%; min-height: 30vh;"
                id="widen"
                bind:this={elem4}
            >
                <IntersectionObserver once element={elem4} let:intersecting>
                    {#if intersecting}
                        <h1
                            style="font-size: 5vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.3vw; padding-left: 5%; margin-bottom: 0;"
                            transition:fade={{ delay: 200, duration: 3500 }}
                        >
                            Where the GTA comes for HVAC/R services
                        </h1>
                        <p
                            style="padding-left: 5%;"
                            transition:fade={{ delay: 200, duration: 1000 }}
                        >
                            Learn more about how we can help you with 15 years
                            experience in heating, ventilation, air
                            conditioning, refrigeration and air purification.
                        </p>
                    {/if}
                </IntersectionObserver>
            </div>
            <MediaQuery query="(max-width: 1280px)" let:matches>
                <IntersectionObserver once element={elem1} let:intersecting>
                    <div class="flexbox" id="phonebye" bind:this={elem1}>
                        {#if intersecting}
                            <section
                                class="dispapp"
                                style="border: 1px solid rgba(255, 255, 255, 0.13); border-left: none; border-bottom: none; "
                                transition:fly={{
                                    delay: 300,
                                    duration: 1000,
                                    x: 100,
                                }}
                            >
                                <img
                                    class="discon"
                                    src="\clock.webp"
                                    alt="clock"
                                />
                                <div style="position: absolute; bottom: 0; ">
                                    <h1
                                        style="text-align: center; padding: 0; margin: 0; padding-bottom: 2vh;"
                                    >
                                        Available 24 Hours
                                    </h1>
                                </div>
                            </section>
                            <section
                                class="dispapp"
                                style="border: 1px solid rgba(255, 255, 255, 0.13); border-bottom: none; border-left: none;"
                                transition:fly={{
                                    delay: 400,
                                    duration: 1000,
                                    x: 100,
                                }}
                            >
                                <img
                                    class="discon"
                                    src="\license.webp"
                                    alt="license"
                                />
                                <div style="position: absolute; bottom: 0; ">
                                    <h1
                                        style="text-align: center; padding: 0; margin: 0; padding-bottom: 2vh;"
                                    >
                                        Licensed and Insured
                                    </h1>
                                </div>
                            </section>
                            <section
                                class="dispapp"
                                style="border: 1px solid rgba(255, 255, 255, 0.19); border-bottom: none; border-left: none;"
                                transition:fly={{
                                    delay: 500,
                                    duration: 1000,
                                    x: 100,
                                }}
                            >
                                <img
                                    class="discon"
                                    src="\calendar.webp"
                                    alt="calendar"
                                    style="height: auto"
                                />
                                <div style="position: absolute; bottom: 0; ">
                                    <h1
                                        style="text-align: center; padding: 0; margin: 0; padding-bottom: 2vh;"
                                    >
                                        Available on Weekends
                                    </h1>
                                </div>
                            </section>
                        {/if}
                    </div>
                </IntersectionObserver>
            </MediaQuery>
        </div>
    </div>
    <div class="flexbox" id="phone">
        <section
            class="dispapp"
            style="border: 1px solid rgba(255, 255, 255, 0.13); border-left: none; border-bottom: none; "
        >
            <img class="discon" src="\clock.webp" alt="clock" />
            <div style="position: absolute; bottom: 0; ">
                <h1
                    style="text-align: center; padding: 0; margin: 0; padding-bottom: 2vh;"
                >
                    Available 24 Hours
                </h1>
            </div>
        </section>
        <section
            class="dispapp"
            style="border: 1px solid rgba(255, 255, 255, 0.13); border-bottom: none; border-left: none;"
        >
            <img class="discon" src="\license.webp" alt="license" />
            <div style="position: absolute; bottom: 0; ">
                <h1
                    style="text-align: center; padding: 0; margin: 0; padding-bottom: 2vh;"
                >
                    Licensed and Insured
                </h1>
            </div>
        </section>
        <section
            class="dispapp"
            style="border: 1px solid rgba(255, 255, 255, 0.19); border-bottom: none; border-left: none;"
        >
            <img
                class="discon"
                src="\calendar.webp"
                alt="calendar"
                style="height: auto"
            />
            <div style="position: absolute; bottom: 0; ">
                <h1
                    style="text-align: center; padding: 0; margin: 0; padding-bottom: 2vh;"
                >
                    Available on Weekends
                </h1>
            </div>
        </section>
    </div>
    <MediaQuery query="(max-width: 1280px)" let:matches>
        <IntersectionObserver once element={elem2} let:intersecting>
            <div class="flexbox" id="types" style="height: 30vw">
                {#if intersecting && !matches}
                    <section
                        class="dispapp"
                        id="residential"
                        transition:fade={{ delay: 0, duration: 500 }}
                    >
                        <!-- <img class="bg" src="\principleairlogo.png" alt="about us" /> -->
                        <div
                            style="position: absolute; bottom: 0;"
                            class="shadow"
                        >
                            <h1>Residential</h1>
                            <p>Making your house a comfortable home</p>
                        </div>
                    </section>
                    <div
                        class="dispapp"
                        id="commercial"
                        transition:fade={{ delay: 250, duration: 500 }}
                    >
                        <div
                            style="position: absolute; bottom: 0;"
                            class="shadow"
                        >
                            <h1>Commercial</h1>
                            <p>Services for your business and property</p>
                        </div>
                    </div>
                    <div
                        class="dispapp"
                        id="industrial"
                        style="height: 30vw;"
                        transition:fade={{ delay: 500, duration: 500 }}
                    >
                        <div
                            style="position: absolute; bottom: 0;"
                            class="shadow"
                        >
                            <h1>Industrial</h1>
                            <p>
                                A custom approach for your facility and sector
                            </p>
                        </div>
                    </div>
                {/if}
            </div>
        </IntersectionObserver>
    </MediaQuery>
    <MediaQuery query="(max-width: 1280px)" let:matches>
        {#if matches}
            <section
                class="dispapp"
                id="residential"
                transition:fade={{ delay: 0, duration: 500 }}
            >
                <!-- <img class="bg" src="\principleairlogo.png" alt="about us" /> -->
                <div style="position: absolute; bottom: 0;" class="shadow">
                    <h1>Residential</h1>
                    <p>Making your house a comfortable home</p>
                </div>
            </section>
            <div
                class="dispapp"
                id="commercial"
                transition:fade={{ delay: 250, duration: 500 }}
            >
                <div style="position: absolute; bottom: 0;" class="shadow">
                    <h1>Commercial</h1>
                    <p>Services for your business and property</p>
                </div>
            </div>
            <div
                class="dispapp"
                id="industrial"
                style="height: 30vw;"
                transition:fade={{ delay: 500, duration: 500 }}
            >
                <div style="position: absolute; bottom: 0;" class="shadow">
                    <h1>Industrial</h1>
                    <p>A custom approach for your facility and sector</p>
                </div>
            </div>
        {/if}
    </MediaQuery>
    <div style="text-align: center;" bind:this={elem2}>
        <h1
            style="font-size: 3vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.3vw; margin: 3vh 0vw;"
        >
            Our Corporate Clients
        </h1>
        <div class="leflex">
            <div class="embla" use:emblaCarouselSvelte={{ options, plugins }}>
                <div class="embla__container">
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/aquablue.webp"
                            alt="aquablue"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/pizzaville.webp"
                            alt="pizzaville"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/van.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/downsview.webp"
                            alt="downsview"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/dup.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/aspenridge.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/best.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/fa.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/cat.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/graywood.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/matera.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/solp.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/icon.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/af.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/pc.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/von.webp"
                            alt="about us"
                        />
                    </div>
                    <div class="embla__slide">
                        <img
                            style="width: 100%; height: 100%"
                            src="/si.webp"
                            alt="about us"
                        />
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div class="" id="offers" style="position: relative; z-index: 3;">
        <!-- <div id="offer1" style="display: none;">
            <h1
                style="font-size: 3vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.3vw; margin: 3vh 0vw;  text-align: center;"
            >
                Special Offer
            </h1>
            <p style="font-size: 2.5vw; line-height: 0.8; letter-spacing: -0.2vw; margin: 3vh 0vw; padding-left: 1vw; text-align: center;">Furnace installation comes with a</p>
            <IntersectionObserver once element={elem3} let:intersecting>
                <div
                    style="position: relative; text-align: center; align-items: center;"
                >
                    <img
                        src="\ecobee.png"
                        alt=""
                        style="width: 100%; position: static; left: 0; right: 0; margin-left: auto; margin-right: auto; padding: 0; margin: 0 0vw;"
                    />
                    {#if intersecting}
                        <p id="free" transition:fade={{ delay: 200 }}>FREE</p>
                        <p id="freeout">FREE</p>
                        <p id="freeout2" transition:fade={{ delay: 200 }}>
                            FREE
                        </p>
                    {/if}
                </div>
            </IntersectionObserver>
            <p
                style="font-size: 2vw; line-height: 0.8; letter-spacing: -0.1vw; margin: 0 0vw; padding-left: 1vw; text-align: center;"
                bind:this={elem3}
            >
                Furnace installation comes with a <b>FREE</b> Ecobee3 Thermostat
            </p>
        </div> -->
        <div id="offer2" style="margin-left: 24vw; margin-right: auto;">
            <h1
                style="font-size: 3vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.3vw; margin: 3vh 0vw; padding-left: 1vw; padding-right: 5vw;"
            >
                Ready to digitally regulate your home or office?
            </h1>
            <p
                style="font-size: 2.5vw; line-height: 0.8; letter-spacing: -0.2vw; margin: 3vh 0vw; padding-left: 1vw;"
            >
                Contact us for a <b>FREE</b> quote!
            </p>
            <div style="width: 60vw;">
                <Contact></Contact>
            </div>
        </div>
    </div>
    <Footer></Footer>
</body>

<style>
    body {
        overflow-x: hidden;
    }
    #logo {
        height: 50vh;
        z-index: 2;
        padding: 10vh;
    }
    svg {
        position: relative;
        height: 100%;
        width: 100%;
        display: block;
        margin-left: auto;
        margin-right: auto;
        z-index: 1;
    }
    path {
        fill: none;
        opacity: 1;
        z-index: 2;
    }
    .bigfront {
        position: relative;
        display: relative;
        align-items: center;
        background-color: transparent;
        z-index: 2;
        width: 100%;
        border-bottom: 1px solid rgba(255, 255, 255, 0.39);
    }
    #introvid {
        position: absolute;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: -2;
    }
    .box {
        position: relative;
        height: 80vh;
        border: 1px solid rgba(255, 255, 255, 0.13);
        border-right: 0;
        z-index: -1;
        top: 0vh;
        flex-grow: 1;
        display: flex;
        flex-direction: column-reverse;
        padding: 0;
        margin: 0;
        z-index: 17;
    }
    .hflex {
        position: absolute;
        top: 0;
        z-index: 3;
        display: flex;
        flex-direction: row;
        width: 100%;
        height: 80vh;
        flex-basis: 0;
        background: rgba(0, 0, 0, 0.5);
    }
    .box p {
        position: absolute;
        padding: 0;
        margin-bottom: 1vh;
        margin-left: 0.5vw;
        color: rgba(255, 255, 255, 0.621);
    }
    .flexbox {
        position: relative;
        display: flex;
        flex-direction: row;
        width: 100%;
    }
    #mimg {
        display: relative;
        flex: 1 1 0px;
        flex-grow: 1;
        border: 1px solid rgba(255, 255, 255, 0.13);
    }
    #mtext {
        flex: 1 1 0px;
        flex-grow: 2;
        border: 1px solid rgba(255, 255, 255, 0.13);
        display: flex;
        flex-direction: column;
        border-left: none;
    }
    .dispapp {
        /* border: 1px solid rgba(255, 255, 255, 0.13); */
        border-right: none;
        justify-content: center;
        display: flex;
        position: relative;
        width: 100%;
    }
    .dispapp h1 {
        padding-left: 1vw;
        font-weight: normal;
        line-height: 0.8;
        letter-spacing: -1px;
        margin-bottom: 0;
        font-size: 1.5vw;
        display: block;
        margin: 0;
        margin-top: 1vw;
    }
    .dispapp p {
        padding-left: 1vw;
        font-size: 0.85vw;
        display: block;
    }
    .discon {
        width: 30%;
        padding: 5vh;
        margin: auto;
        margin-bottom: 5vh;
        display: block;
        height: auto;
    }
    .leflex {
        flex: 1 1 0px;
        flex-grow: 1;
        border: 1px solid rgba(255, 255, 255, 0.13);
    }
    /* .full-size {
        width: 100%;
        height: 100%;
    } */
    .embla {
        overflow: hidden;
    }
    .embla__container {
        display: grid;
        grid-auto-flow: column;
        grid-auto-columns: 16.5%;
    }
    .embla__slide {
        flex: 0 0 100%;
        min-width: 0;
        border: 1px solid rgba(255, 255, 255, 0.13);
        border-top: none;
        border-left: none;
        aspect-ratio: 1/1;
    }
    #offer1 {
        display: relative;
        flex: 1 1 0px;
        flex-grow: 1;
        border: 1px solid rgba(255, 255, 255, 0.13);
        border-top: none;
    }
    #offer2 {
        flex: 1 1 0px;
        flex-grow: 2;
        border: 1px solid rgba(255, 255, 255, 0.13);
        display: flex;
        flex-direction: column;
        border-left: none;
        border-top: none;
    }
    #free {
        padding: 0;
        margin: 0;
        position: absolute;
        z-index: -1;
        font-family: "Archivo Black", sans-serif;
        font-size: 11.75vw;
        top: 20%;
        left: 0%;
        letter-spacing: -0.5vw;
        /* color: rgba(255, 255, 255, 0.13);  */
    }
    /*
    #freeout { 
        padding: 0; margin: 0; 
        position: absolute;
        z-index: 3; 
        font-family: "Archivo Black", sans-serif;
        font-size: 11.75vw;
        top: 20%; left: 0%; 
        -webkit-text-fill-color: transparent;
        -webkit-text-stroke: 0.4vw;
        letter-spacing: -0.5vw;
    }
    */
    #freeout2 {
        padding: 0;
        margin: 0;
        position: absolute;
        z-index: 2;
        font-family: "Archivo Black", sans-serif;
        font-size: 11.75vw;
        top: 20%;
        left: 0%;
        -webkit-text-fill-color: transparent;
        -webkit-text-stroke: 0.3vw;
        letter-spacing: -0.5vw;
        /* color: rgb(114, 114, 114);  */
        /* color: rgb(32, 32, 32);  */
        color: rgb(4, 189, 102);
    }
    #residential {
        background-image: url("/residential.webp");
        background-size: cover;
    }
    #commercial {
        background-image: url("/ind.webp");
        background-position: center;
        background-size: cover;
    }
    #industrial {
        background-image: url("/commm.webp");
        background-position: center;
        background-size: cover;
    }
    .shadow {
        background-color: rgba(0, 0, 0, 0.778);
        width: 100%;
    }
    #phone {
        display: none;
    }
    #mimg video {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
    #mtext {
        min-height: 65vh;
    }
</style>
