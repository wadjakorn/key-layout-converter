<script lang="ts">
  import Converter from './lib/Converter.svelte';
</script>

<main>
  <h1>de = กำ</h1>

  <p>ลืมเปลี่ยนภาษาใช่ไหม? แปะตรงนี้แล้วเลือกภาษาได้เลย</p>

  <div class="card">
    <Converter />
  </div>

  <p>
    Check out <a href="https://github.com/wadjakorn/key-layout-converter" target="_blank" rel="noreferrer">Wadjakorn Github</a>
  </p>

  <p class="read-the-docs">
    by wadjakorn.me
  </p>
</main>

<style>
  .read-the-docs {
    color: #888;
  }
</style>