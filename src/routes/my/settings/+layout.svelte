<script>
    /** @type {import('./$types').PageData} */
    export let data;
</script>

<div class="pl-6 pt-4">
    <ul class="menu bg-base-100 w-56 p-2 rounded-box">
        <li>
          <a href="/my/settings/theme">
            <i class='bx bx-palette' ></i>
          Theme
          </a>
        </li>
        <li>
          <a href="/my/settings/">
            <i class='bx bx-grid-alt' ></i>
            Preference
          </a>
        </li>
        <li>
          <a href="/my/settings/">
            <i class='bx bx-user-pin' ></i>
            Item 3
          </a>
        </li>
      </ul>
</div>

<slot />
