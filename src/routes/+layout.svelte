<script>
  import { page } from "$app/stores";
  import "./styles.css";
</script>

<div class="app">
  <header>
    <div class="corner">
      <a href="https://bornjre.github.io"> Blog </a>
    </div>

    <nav>
      <ul>
        <li aria-current={$page.url.pathname === "/" ? "page" : undefined}>
          <a href="/">Home</a>
        </li>

        <li
          aria-current={$page.url.pathname || "".includes("/propaganda")
            ? "page"
            : undefined}
        >
          <a href="/propaganda">propaganda</a>
        </li>

        <li aria-current={$page.url.pathname === "/about" ? "page" : undefined}>
          <a href="/about">About</a>
        </li>
      </ul>
    </nav>
  </header>

  <main>
    <slot />
  </main>

  <footer>
    <p>Made with hands ✋</p>
  </footer>
</div>

<style>
  .app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  main {
    flex: 1;
    display: flex;
    flex-direction: column;
    padding: 1rem;
    width: 100%;
    max-width: 64rem;
    margin: 0 auto;
    box-sizing: border-box;
  }

  footer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 12px;
  }

  @media (min-width: 480px) {
    footer {
      padding: 12px 0;
    }
  }

  header {
    --background: rgba(255, 255, 255, 0.7);
    display: flex;
    justify-content: space-between;
    background: var(--background);
    background-size: contain;
  }

  .corner {
    width: 3em;
    height: 3em;
  }

  .corner a {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
  }

  nav {
    display: flex;
    justify-content: center;
  }

  ul {
    position: relative;
    padding: 0;
    margin: 0;
    height: 3em;
    display: flex;
    justify-content: center;
    align-items: center;
    list-style: none;
    border-radius: 4px;
  }

  li {
    position: relative;
    height: 100%;
  }

  li[aria-current="page"]::before {
    --size: 6px;
    content: "";
    width: 0;
    height: 0;
    position: absolute;
    top: 0;
    left: calc(50% - var(--size));
    border: var(--size) solid transparent;
    border-top: var(--size) solid var(--color-theme-1);
  }

  nav a {
    display: flex;
    height: 100%;
    align-items: center;
    padding: 0 0.5rem;
    color: var(--color-text);
    font-weight: 700;
    font-size: 0.8rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    text-decoration: none;
    transition: color 0.2s linear;
  }

  a:hover {
    color: var(--color-theme-1);
  }
</style>
