<script>
    import { page } from '$app/stores';
  </script>
  
  <header>
    <nav>
      <ul>
        <li class:active={$page.url.pathname === '/'}>
          <a href="/">Home</a>
        </li>
        <li class:active={$page.url.pathname === '/about'}>
          <a href="/about">About</a>
        </li>
        <li class:active={$page.url.pathname === '/contact'}>
          <a href="/contact">Contact</a>
        </li>
      </ul>
    </nav>
  </header>
  
  <style>
    header {
      background-color: #f0f0f0;
      padding: 1rem;
    }
  
    ul {
      list-style-type: none;
      padding: 0;
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
    }
  
    li {
      margin: 0.5rem;
    }
  
    a {
      text-decoration: none;
      color: #333;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      transition: background-color 0.3s;
    }
  
    a:hover, .active a {
      background-color: #0066cc;
      color: white;
    }
  
    @media (max-width: 768px) {
      ul {
        flex-direction: column;
        align-items: center;
      }
  
      li {
        margin: 0.25rem 0;
      }
    }
  </style>