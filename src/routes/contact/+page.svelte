<script>
    // @ts-ignore
    import Navbar from "../template/nav.svelte";
    import Navphone from "../template/navphone.svelte";
    import Footer from "../template/footer.svelte";
    import Contact from "../template/contact.svelte";
    import MediaQuery from "../MediaQuery.svelte";

    import IntersectionObserver from "svelte-intersection-observer";
    import { fade, draw, fly, crossfade, blur } from "svelte/transition";
    /**
     * @type {any}
     */
    let elem1;
</script>

<MediaQuery query="(max-width: 1280px)" let:matches>
    {#if matches}
        <style>
            h1 {
                font-size: 5vh !important;
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
            #bgp {
                padding-top: 13vh !important;
            }
            body {
                overflow-x: hidden !important;
            }
            #bigpad {
                padding-top: 12vh !important;
            }
            .flexbox {
                flex-direction: column-reverse !important;
                justify-content: space-around;
            }
            .flexchild {
                width: 100% !important;
            }
            p {
                width: 100% !important;
            }
            #contactf {
                display: block !important;
                padding-top: 5vh !important;
                padding-bottom: 10vh !important;
                background: none !important;
            }
            hr {
                position: relative;
                width: 200vw;
                left: -50vw;
                padding: 0;
                margin: 0;
                border: 1px solid rgba(255, 255, 255, 0.13);
            }
            #cont { 
                margin-bottom: 5vh !important; 
            }
            #phonebruh { 
                min-height: 70vh !important; 
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
    <MediaQuery query="(max-width: 1280px)" let:matches>
        <IntersectionObserver once element={elem1} let:intersecting>
            <div
                style="height: 100%; display: flex; flex-direction: column; "
                bind:this={elem1}
            >
                <div class="flexbox" id="bgp" style="padding-top: 7vh;">
                    <div class="flexchild" id="contactf">
                        <h1
                            id="cont"
                            style="font-size: 3vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.3vw; margin-top: 7vh; margin-bottom: -3vh;"
                        >
                            Contact Us
                        </h1>
                        <Contact></Contact>
                    </div>
                    <div
                        class="flexchild"
                        style="margin-top: auto; margin-bottom: auto;"
                        id="phonebruh"
                    >
                        {#if intersecting || matches}
                            <h1
                                style="font-size: 3vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.3vw; margin: 3vh 0vw; width: 70%;"
                                transition:fly={{
                                    delay: 100,
                                    duration: 1000,
                                    y: -1000,
                                }}
                            >
                                No matter the project, Principle Air is there.
                            </h1>
                            <p transition:fade={{ delay: 700, duration: 500 }}>
                                Our team is available Monday to Friday between
                                8:00 am – 5:00 pm. For emergency matters, we are
                                also available on the weekends and after hours.
                                We serve Toronto and the GTA.
                            </p>
                            <p style="margin-bottom: 0; padding-bottom: 1vh;" transition:fade={{ delay: 800, duration: 500 }}>
                                416-271-5618
                            </p>
                            <p style="margin-top: 0; padding-top: 0;" transition:fade={{ delay: 900, duration: 500 }}>
                                647-722-1120
                            </p>
                            <p transition:fade={{ delay: 1000, duration: 500 }}>
                                info@principleair.com
                            </p>
                        {/if}
                    </div>
                </div>
                <div style="width: 100%: position: absolute; margin-top: auto;">
                    <Footer></Footer>
                </div>
            </div>
        </IntersectionObserver>
    </MediaQuery>
</body>

<style>
    /* body {
        display: flex;
        min-height: 100vh;
        flex-direction: column;
        justify-content: flex-start;
    } */
    body {
        width: 100%;
        height: 100vh;
    }
    .flexbox {
        position: relative;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        width: 80vw;
        margin: 0;
        padding: 0;
        margin-left: auto;
        margin-right: auto;
        padding-top: 2vh;
    }
    .flexchild {
        flex: 1 1 0px;
    }
    h1 {
        padding-left: 3vw;
    }
    p {
        padding: 2vh 0vw;
        padding-left: 3vw;
        width: 50%;
    }
    #phone {
        display: none;
    }
</style>
