<template>
  <div id="about-page" class="page-wrapper about-page content-page">
    <site-hero
      title="About Us"
      subtitle="Example About Page"
      image="/uploads/about-hero.jpg"
    ></site-hero>
    <main-section theme="sidebar-right">
      <template v-slot:default>
        <div class="content">
          <h3>Fake Heading</h3>
          
          <p>
              Hello there, and welcome to my little corner of the internet! I'm a lover of all things math, art, and technology, and this blog is my playground for exploring the fascinating connections between these worlds.          </p>
          
        </div>
        <posts-grid :per-row="1" :number="2" />
      </template>
    </main-section>
  </div>
</template>
