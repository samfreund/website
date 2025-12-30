<script setup lang="ts">
import Button from "./components/Button.vue";
import GridSection from "./components/GridSection.vue";

const navLinks = [
  {
    href: "#about",
    label: "About",
    icon: "fa-solid fa-user",
  },
  {
    href: "#skills",
    label: "Skills",
    icon: "fa-solid fa-code",
  },
  {
    href: "#projects",
    label: "Projects",
    icon: "fa-solid fa-folder-open",
  },
  {
    href: "#contact",
    label: "Contact",
    icon: "fa-solid fa-envelope",
  },
];

const skills = [
  {
    icon: "fa-solid fa-code",
    title: "Frontend Development",
    description: "Building responsive and interactive user interfaces with modern frameworks.",
  },
  {
    icon: "fa-solid fa-server",
    title: "Backend Development",
    description: "Creating scalable server-side applications and RESTful APIs.",
  },
  {
    icon: "fa-solid fa-database",
    title: "Database Design",
    description: "Designing and optimizing database schemas for performance and reliability.",
  },
  {
    icon: "fa-solid fa-mobile-alt",
    title: "Mobile Development",
    description: "Developing cross-platform mobile applications with native performance.",
  },
  {
    icon: "fa-solid fa-cloud",
    title: "Cloud Services",
    description: "Deploying and managing applications on cloud platforms.",
  },
  {
    icon: "fa-solid fa-cog",
    title: "DevOps",
    description: "Automating workflows and implementing CI/CD pipelines.",
  },
];

const projects = [
  {
    icon: "fa-solid fa-laptop-code",
    title: "Project One",
    description: "A brief description of your first project and the technologies used to build it.",
  },
  {
    icon: "fa-solid fa-rocket",
    title: "Project Two",
    description: "A brief description of your second project and the impact it had.",
  },
  {
    icon: "fa-solid fa-chart-line",
    title: "Project Three",
    description: "A brief description of your third project and what makes it unique.",
  },
];

const socialLinks = [
  {
    href: "https://github.com/samfreund/",
    icon: "fab fa-github",
    label: "GitHub",
  },
  {
    href: "https://www.linkedin.com/in/samuel-freund/",
    icon: "fab fa-linkedin-in",
    label: "LinkedIn",
  },
  {
    href: "mailto:samf.236@proton.me",
    icon: "fa-solid fa-envelope",
    label: "Email",
  },
];
</script>

<template>
  <div id="page-wrapper" class="h-screen overflow-y-auto scroll-smooth">
    <header
      id="header"
      class="bg-zinc-900/80 backdrop-blur-md flex items-center justify-between sticky top-0 w-full z-50 border-b border-zinc-700/50 px-4 md:px-8"
    >
      <a href="#" class="flex items-center gap-3 py-2 group">
        <img
          src="/images/headshot.png"
          alt="Sam Freund"
          class="w-10 h-10 rounded-full group-hover:scale-110 transition-transform duration-300"
        />
        <span class="font-bold text-xl hidden sm:block text-white">
          Sam Freund
        </span>
      </a>
      <div>
        <!-- Mobile menu button -->
        <button
          class="p-3 hover:bg-zinc-700/50 rounded-lg cursor-pointer flex md:!hidden transition-colors anchor/my-anchor"
          popovertarget="mobile-nav"
          aria-label="Open mobile navigation menu"
        >
          <i class="fa-solid fa-bars text-xl"></i>
        </button>

        <div class="relative">
          <div
            popover
            id="mobile-nav"
            class="bg-zinc-900/95 backdrop-blur-lg transition-opacity starting:open:opacity-0 open:opacity-100 opacity-0 duration-300 transition-discrete open:flex open:flex-col md:open:hidden items-center justify-center gap-2 anchored/my-anchor anchored-bottom-span-left overflow-clip p-2 rounded-b-2xl"
          >
            <a
              v-for="link in navLinks"
              :key="link.href"
              :href="link.href"
              class="flex items-center gap-3 px-6 py-4 text-xl text-white hover:text-brand-yellow transition-colors"
            >
              <i :class="link.icon"></i>
              {{ link.label }}
            </a>
          </div>
        </div>
      </div>

      <!-- Desktop nav -->
      <nav id="nav" class="hidden md:flex items-center gap-1">
        <a
          v-for="link in navLinks"
          :key="link.href"
          :href="link.href"
          class="flex items-center gap-2 px-4 py-2 rounded-lg hover:bg-zinc-700/50 hover:text-brand-yellow transition-all duration-200"
        >
          <i :class="[link.icon, 'text-sm opacity-70']"></i>
          {{ link.label }}
        </a>
      </nav>
    </header>

    <section
      id="about"
      class="flex flex-col min-h-[calc(100vh_-_56px)] md:justify-center items-center p-8 md:p-16 relative overflow-hidden"
    >
      <div
        class="flex justify-center md:justify-start flex-col md:flex-row items-center gap-8"
      >
        <span class="self-center md:self-initial shrink">
          <img
            src="/images/headshot.png"
            alt="Sam Freund"
            class="max-w-48 md:max-w-80 rounded-full drop-shadow-2xl transition-transform duration-500 hover:scale-105"
          />
        </span>
        <header
          class="flex flex-col gap-6 items-center md:items-start justify-center text-center md:text-start"
        >
          <h1
            class="text-5xl md:text-6xl font-bold drop-shadow-lg font-heading"
          >
            Hi, I'm <span class="text-brand-yellow">Sam Freund</span>
          </h1>
          <div
            class="text-xl md:text-2xl max-w-128 text-zinc-300 leading-relaxed"
          >
            I'm a software developer passionate about building elegant solutions
            to complex problems. Welcome to my portfolio.
          </div>
          <div class="flex gap-4 self-center md:self-start">
            <Button
              href="#projects"
              variant="primary"
              size="lg"
              class="rounded-xl"
            >
              View My Work
            </Button>
            <Button
              href="#contact"
              variant="outline"
              size="lg"
              class="rounded-xl"
            >
              Get in Touch
            </Button>
          </div>
        </header>
      </div>
      <a
        href="#skills"
        class="absolute bottom-8 p-4 text-brand-yellow/70 hover:text-brand-yellow hover:translate-y-1 transition-all duration-300 animate-bounce"
      >
        <i class="fa-solid fa-chevron-down text-2xl"></i>
      </a>
    </section>

    <GridSection
      id="skills"
      description="I specialize in full-stack development with expertise across modern technologies and frameworks. Here are some of the areas where I excel."
      :features="skills"
      :columns="2"
      show-scroll-indicator
      scroll-target="#projects"
    >
      <template #title>
        Skills & <span class="text-brand-yellow">Expertise</span>
      </template>
    </GridSection>

    <GridSection
      id="projects"
      description="Here are some of my recent projects that showcase my skills and experience. Each project represents a unique challenge and learning opportunity."
      :features="projects"
      :columns="3"
      reverse-cards
    >
      <template #title>
        Featured <span class="text-brand-yellow">Projects</span>
      </template>
    </GridSection>

    <section
      id="contact"
      class="py-20 px-8 bg-zinc-900 border-t border-zinc-700"
    >
      <div class="max-w-4xl mx-auto text-center">
        <h2 class="text-4xl font-bold mb-6 font-heading">
          Get in <span class="text-brand-yellow">Touch</span>
        </h2>
        <p class="text-xl text-zinc-300 mb-8 max-w-2xl mx-auto">
          I'm always interested in new opportunities and collaborations. Feel
          free to reach out!
        </p>
        <div class="flex justify-center gap-6 mb-8">
          <a
            v-for="link in socialLinks"
            :key="link.href"
            :href="link.href"
            class="flex items-center gap-2 px-6 py-3 bg-zinc-800 hover:bg-zinc-700 rounded-lg transition-colors"
          >
            <i :class="[link.icon, 'text-xl']"></i>
            <span>{{ link.label }}</span>
          </a>
        </div>
      </div>
    </section>

    <footer id="footer" class="py-8 px-8 bg-zinc-800">
      <div
        class="max-w-6xl mx-auto flex flex-col md:flex-row items-center justify-between gap-4"
      >
        <div class="flex items-center gap-4">
          <img
            src="/images/headshot.png"
            class="w-10 h-10 rounded-full hover:scale-110 transition-transform duration-300"
            alt="Sam Freund"
          />
          <span class="font-semibold text-lg">Sam Freund</span>
        </div>
        <p class="text-sm text-zinc-400">
          &copy;{{ new Date().getFullYear() }} Sam Freund. All rights
          reserved.
        </p>
      </div>
    </footer>
  </div>
</template>