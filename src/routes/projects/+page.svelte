<script>
    import Navbar from "../template/nav.svelte";
    import Navphone from "../template/navphone.svelte";
    import Footer from "../template/footer.svelte";
    import Projecte from "./projecteven.svelte";
    import Projecto from "./projectodd.svelte";

    let projects = [
        {
            name: "Dehumidification Units ",
            image: "/dec.webp",
            description: [
                "Specialty unit for pools, featuring control over humidity levels in pool areas, improving overall air quality",
                "We offer highly customizable solutions with high durability and long lifespans",
                "We specialize in installing, troubleshooting, and maintaining this unit",
            ],
            vid: 0,
            namet: "Variable Speed Drives",
            imaget: "/abb.webp",
            descriptiont: [
                "Installation service and retrofitting of Variable Frequency Drives (VFDs)",
                "Significant advancement in energy efficiency and operational flexibility for heating, ventilation, and air-conditioning systems",
                "Our services include the supply, startup, commissioning, and service of VFDs",
            ],
            vidt: 0,
        },
        {
            name: "Gas Lines",
            image: "/gas.webp",
            description: [
                "Our gas line installation services provide reliable and safe solutions for residential, commercial, and industrial properties",
                "Our services include new installations, rectifying infractions, replacements, upgrades, and repairs",
            ],
            vid: 0,
            namet: "Package Rooftop Units",
            imaget: "/york.webp",
            descriptiont: [
                "Any Brand, Any Model: We work with all major HVAC brands and models whether it be a new installation, retrofit or service",
                "Our services include maintenance proposals, on-site evaluations, and energy audits",
            ],
            vidt: 0,
        },
        {
            name: "Split Systems",
            image: "/ladder.mp4",
            description: [
                "Whether it be a new installation, retrofit, or service, our team is here to assist with the the supply, installation, maitenance, and service to make your system work efforlessly",
                "Our residential an commercial mini-splits solutions are ideal for individual room control and comfortability",
            ],
            vid: 1,
            namet: "Air Handling Units",
            imaget: "/daikin.webp",
            descriptiont: [
                "A highly innovative and energy-efficient solution for commercial and industrail applications",
                "The various configurations and durability offer both flexibility and reliability",
                "We install, maintain, and troubleshoot various air handling units, make-up air units, and ecology units",
            ],
            vidt: 0,
        },
        {
            name: "Hydronic Boilers",
            image: "/boiler.webp",
            description: [
                "Energy efficient heating solution for residential and commercial applications",
                "Our professional installation will ensure quiet and seamless operation, providing a desired environment",
                "We specialize in the installation, replacement, service, and maintenance of hydronic boilers",
            ],
            vid: 0,
            namet: "Floor Heating",
            imaget: "/floor.webp",
            descriptiont: [
                "Our specialty underfloor heating services offer a comfortable, uniform warmth distrubtion across the entire floor",
                "We offer the complete commissioning, servicing, and maintenance of these systems",
            ],
            vidt: 0,
        },
    ];
    let cnt = 0;
    let good = true;
    import MediaQuery from "../MediaQuery.svelte";

    import IntersectionObserver from "svelte-intersection-observer";
    import { fade, draw, fly, crossfade, blur } from "svelte/transition";
    import { cubicInOut } from "svelte/easing";
    /**
     * @type {any}
     */
    let elem1;
    /**
     * @type {any}
     */
    let elem2;
</script>

<svelte:head>
    <title>Our Projects</title>
    <meta name="title" content="Our Projects" />
    <meta
        name="description"
        content="Explore the wide variety of projects in our catalogue. The catalogue showcases all our services, including residential, commercial, and industrial applications."
    />
    <meta
        name="keywords"
        content="HVAC/R, building automation, commercial, industrial, residential, experienced"
    />
    <meta name="robots" content="index, follow" />
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta name="language" content="English" />
    <meta name="author" content="Pavithran Chelliahpillai" />
</svelte:head>

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
            #phone h1 {
                font-size: 3vh !important;
            }
            body {
                overflow-x: hidden !important;
            }
            .flexbox {
                display: block !important;
            }
            #bgp {
                padding-top: 12vh !important;
            }
            img {
                object-fit: cover !important;
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
    <IntersectionObserver once element={elem1} let:intersecting>
        <div
            class="flexbox"
            id="bgp"
            style="padding-top: 7vh;"
            bind:this={elem1}
        >
            {#if intersecting}
                <div
                    class="flexchild"
                    style="border-left: 0; min-height: 22vh;"
                >
                    <h1
                        style="font-size: 3vw; font-weight: normal; line-height: 0.8; letter-spacing: -0.3vw; margin: 3vh 0vw;"
                        transition:fade={{
                            delay: 200,
                            duration: 750,
                            easing: cubicInOut,
                        }}
                    >
                        Our Projects
                    </h1>
                    <p
                        id="proj"
                        style="width: 50%;"
                        transition:fade={{ delay: 400, duration: 350 }}
                    >
                        Explore the wide variety of projects in our catalogue.
                        The catalogue showcases all our services, including
                        residential, commercial, and industrial applications.
                    </p>
                </div>
            {/if}
            <div class="flexchild" style="width: 100%; flex-grow: 2;"></div>
        </div>
    </IntersectionObserver>
    <MediaQuery query="(max-width: 1280px)" let:matches>
        {#each projects as project, idx}
            {#if idx % 2 == 0 && !matches}
                <Projecte {project} />
            {:else}
                <Projecto {project} />
            {/if}
        {/each}
        {#if matches}
            <style>
                #proj {
                    width: 100% !important;
                }
            </style>
        {/if}
    </MediaQuery>
    <Footer></Footer>
</body>

<style>
    body {
        overflow-x: hidden;
    }
    .flexbox {
        position: relative;
        display: flex;
        flex-direction: row;
        width: 100%;
    }
    .flexchild {
        position: relative;
        /* height: 50vh; */
        border: 1px solid rgba(255, 255, 255, 0.13);
        border-right: 0;
        top: 0vh;
        flex-grow: 1;
        padding: 0;
        margin: 0;
        padding-left: 2vw;
    }
    #phone {
        display: none;
    }
    #proj {
        width: 50%;
    }
</style>
