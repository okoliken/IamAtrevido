<script lang="ts">
  import { concurrent } from "svelte-typewriter";
  import "animate.css";
  import { fade, fly } from "svelte/transition";
  import AtAvatar from "./lib/AtAvatar.svelte";
  import Socials from "./lib/Socials.svelte";
  import { Button, Card, Form, Input } from "spaper";
  // import { success, danger } from "spaper/components/Toast";


  // utility functions
  const project_img = (name: string) => {
    return new URL(`./assets/projects/${name}.png`, import.meta.url).href;
  };
  const getImageUrlSvg = (name: string) => {
    return new URL(`./assets/${name}.svg`, import.meta.url).href;
  };
  //

  // contents

  let stack: string[] = [
    "html",
    "css",
    "js",
    "ts",
    "tailwind",
    "vue",
    "svelte",
    "nuxt",
    "vuetify",
  ];

  interface Projects {
    title: string;
    content: string;
    img: string;
    btnText: string;
    link: string;
  }

  let projects: Projects[] = [
    {
      title: "EA Advisory",
      content: "Source the best deals for Investment.",
      img: "advisory",
      btnText: "Check it out",
      link: "https://eacadvisory.emergingafricagroup.com/",
    },
    {
      title: "Fundall Business",
      content: "Banking for the self-employed",
      img: "business",
      btnText: "Check it out",
      link: "https://business.fundall.io/",
    },
    {
      title: "EA Trustees",
      content: "Secure your lifetime wealth with Emerging Africa Legacy.",
      img: "trustee",
      btnText: "Check it out",
      link: "http://eatrustees.emergingafricagroup.com/",
    },
    {
      title: "CreditPRO SME",
      content:
        "We build long lasting relationships with our small business customers on a mutually beneficial ground",
      img: "creditpro",
      btnText: "Check it out",
      link: "https://app.creditprosme.com/",
    },
    {
      title: "Fundall - Digitizing finance for everyone",
      content:
        "Access tools, education, and business support you need to start, manage and improve your financial lifestyle.",
      img: "fundall",
      btnText: "Check it out",
      link: "https://fundall.io/",
    },

    {
      title: "Fundall Web App",
      content: "Web application for fundall.",
      img: "app-fundall",
      btnText: "Check it out",
      link: "https://app.fundall.io/",
    },
  ];

  let more_project: Projects[] = [
    {
      title: "Shortly",
      content: "More than just shorter links",
      img: "shortly",
      btnText: "Check it out",
      link: "https://urlshortly-vue.netlify.app/",
    },
    {
      title: "Image Gallery",
      content: "More than just shorter links",
      img: "image-gallery",
      btnText: "Check it out",
      link: "https://urlshortly-vue.netlify.app/",
    },
    {
      title: "Huddle",
      content: "Build the community your Fans will love",
      img: "huddle",
      btnText: "Check it out",
      link: "https://huddles-tw.netlify.app/",
    },

    {
      title: "KSBTech",
      content:
        "Buy and sell giftcards and crypto at the best rates. (I worked on the frontend admin for the project)",
      img: "ksbtech",
      btnText: "Check it out",
      link: "https://ksbtech.com.ng/",
    },

    {
      title: "Netflix clone",
      content: "Netflix clone built with vue3, tailwind, TMDB and IMDB API",
      img: "netflix",
      btnText: "Check it out",
      link: "https://v-netflix-clone.netlify.app/",
    },
  ];
  //

  const show_more = (items: Projects[]) => {
    projects = [...projects, ...items];
  };
  const show_less = () => {
    projects = projects.slice(5, 11);
  };

  $: showMoreOrLess = projects.length === 6;
</script>

<div id="top">
  <Socials />
</div>
<main class="container at-flexbox">
  <div class="at-flexbox at-8">
    <AtAvatar />
  </div>

  <div>
    <p
      class="animate__animated animate__delay-1s animate__repeat-2 animate__wobble"
    >
      Hey!,
    </p>
    <h1 use:concurrent={{ interval: 30 }}>
      I'm Okoli Jahbuchim Jeff, a self-taught front-end developer.
    </h1>
    <Button
      class="animate__animated animate__jello animate__delay-1s animate__repeat-2"
      href="https://drive.google.com/file/d/1JgoHUPe8s8h2sT1FIZIDq_VHHt4Eq8wn/view?usp=share_link"
      target="_blank"
      size="large">View my resume</Button
    >
  </div>

  <div class="at-profile">
    <h2>Who am I</h2>
    <p use:concurrent={{ interval: 30 }}>
      I am a software developer who pays close attention to details and loves
      working on the part of software that users interact with, known as
      frontend development. Creating beautiful and easy-to-use websites and
      applications is my passion, and I believe that I would be a great fit for
      your organization.
    </p>
  </div>

  <div class="at-tech--tools">
    <h2>Skill & Tools</h2>
    <div class="row">
      {#each stack as tech_stack (tech_stack)}
        <img
          class="col-5 sm-3 md-2 margin-small shadow hover-shadow"
          src={getImageUrlSvg(tech_stack)}
          alt="Vue.js"
        />
      {/each}
    </div>
  </div>

  <div class="at-projects">
    <h2>Hand-picked projects <br /> for you to see</h2>
    <div class="at-grid">
      {#each projects as project (project)}
        <div in:fly={{ y: 200, duration: 2000 }} out:fade>
          <Card
            class="border border-primary"
            title={project.title}
            image={project_img(project.img)}
          >
            {project.content}
            <p slot="bottom">
              <Button href={project.link} target="_blank"
                >{project.btnText}</Button
              >
            </p>
          </Card>
        </div>
      {/each}
    </div>
    <center class="at-8">
      {#if showMoreOrLess}
        <Button on:click={() => show_more(more_project)} size="large"
          >Show more</Button
        >
      {/if}
    </center>
  </div>

  <div class="at-contact-me margin-bottom-small">
    <h2>Contact me</h2>
    <form action="https://formspree.io/f/mvonlybp" class="w-100" method="post">
      <Input
        name="name"
        placeholder="Enter fullname"
        class="margin-bottom-small w-100"
      />
      <Input
        name="email"
        placeholder="Email address"
        class="margin-bottom-small w-100"
      />
      <Input name="message" placeholder="Message" type="textarea" />

      <Button block nativeType="submit" type="primary" class="margin-top-small"
        >Send message</Button
      >
    </form>
  </div>
  <div class="to-top">
    <Button href="#top">^</Button>
  </div>
</main>

<style>
  h2 {
    margin: 30px 0px;
  }
  .w-100 {
    width: 100%;
    max-width: 900px;
  }
  .at-contact-me {
    width: 100%;
    max-width: 500px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
  :global(html) {
    scroll-behavior: smooth;
  }
  :global(input) {
    width: 100%;
    max-width: 500px;
  }
  :global(textarea) {
    width: 100%;
    max-width: 500px;
  }
  .to-top {
    padding: 0.6em 1em;
    border-top-left-radius: 185px 160px;
    border-top-right-radius: 200px 195px;
    border-bottom-right-radius: 160px 195px;
    border-bottom-left-radius: 185px 190px;
    position: fixed;
    bottom: 5%;
    right: 0%;
  }
  .at-flexbox {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .at-8 {
    margin: 50px 0;
  }

  .at-profile {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    width: 100%;
    height: 100%;
    margin: 10px 0;
  }

  .at-profile p {
    line-height: 30px;
  }

  .at-grid {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 15px;
  }

  @media (min-width: 500px) {
    .at-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 15px;
    }
  }

  @media (min-width: 700px) {
    .at-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 15px;
    }
  }
</style>
