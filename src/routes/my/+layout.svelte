<script>
    import { onMount } from "svelte";
    let root;
    let search;
  //   function handleKeydown(event) {
  //     if (event.ctrlKey && event.key === 'k') {
  //       document.body.classList.remove("shrink");
  //       search.lastElementChild.focus(); 
  //     }
  //         if (event.key == "Escape") {
  //       document.body.classList.toggle("shrink"); 
  //       setTimeout(moveActiveTab, 400)
        
  //   }
  // }
    onMount(() => {
      const shrink_btn = root.querySelector(".shrink-btn");
      search = root.querySelector(".search");
      const sidebar_links = root.querySelectorAll(".sidebar-links a");
      const active_tab = root.querySelector(".active-tab");
      const shortcuts = root.querySelector(".sidebar-links h4");
      const tooltip_elements = root.querySelectorAll(".tooltip-element");
  
      let activeIndex;
      
      shrink_btn.addEventListener("click", () => {
        document.body.classList.toggle("shrink");
        setTimeout(moveActiveTab, 400);
  
        shrink_btn.classList.add("hovered");
  
        setTimeout(() => {
          shrink_btn.classList.remove("hovered");
        }, 500);
      });
  
      search.addEventListener("click", () => {
        document.body.classList.remove("shrink");
        search.lastElementChild.focus();
      });
  
      function moveActiveTab() {
        let topPosition = activeIndex * 58 + 2.5;
  
        if (activeIndex > 3) {
          topPosition += shortcuts.clientHeight;
        }
  
        active_tab.style.top = `${topPosition}px`;
      }
  
      function changeLink() {
        sidebar_links.forEach((sideLink) => sideLink.classList.remove("active"));
        this.classList.add("active");
  
        activeIndex = this.dataset.active;
  
        moveActiveTab();
      }
  
      sidebar_links.forEach((link) => link.addEventListener("click", changeLink));
  
      function showTooltip() {
        let tooltip = this.parentNode.lastElementChild;
        let spans = tooltip.children;
        let tooltipIndex = this.dataset.tooltip;
  
        Array.from(spans).forEach((sp) => sp.classList.remove("show"));
        spans[tooltipIndex].classList.add("show");
  
        tooltip.style.top = `${
          (100 / (spans.length * 2)) * (tooltipIndex * 2 + 1)
        }%`;
      }
  
      tooltip_elements.forEach((elem) => {
        elem.addEventListener("mouseover", showTooltip);
      });
    });
    function moveActiveTab() {
      let topPosition = activeIndex * 58 + 2.5;
  
      if (activeIndex > 3) {
        topPosition += shortcuts.clientHeight;
      }
  
      active_tab.style.top = `${topPosition}px`;
    }
    function shrink() {
      document.body.classList.toggle("shrink");
      setTimeout(moveActiveTab, 400);
  
      shrink_btn.classList.add("hovered");
  
      setTimeout(() => {
        shrink_btn.classList.remove("hovered");
      }, 500);
    }
    function search_func() {
      document.body.classList.remove("shrink");
      search.lastElementChild.focus();
    }
    function showTooltip() {
      let tooltip = this.parentNode.lastElementChild;
      let spans = tooltip.children;
      let tooltipIndex = this.dataset.tooltip;
  
      Array.from(spans).forEach((sp) => sp.classList.remove("show"));
      spans[tooltipIndex].classList.add("show");
  
      tooltip.style.top = `${
        (100 / (spans.length * 2)) * (tooltipIndex * 2 + 1)
      }%`;
    }
  </script>
  
  <!-- <svelte:window on:keydown={handleKeydown}/> -->
  <div bind:this={root}>
    
    <nav >
      <div class="sidebar-top">
        <span class="shrink-btn" >
          <i class="bx bx-chevron-left" />
        </span>
        <img src="/logo.png" class="logo" alt="" />
        <h3 class="hide">I-snip</h3>
      </div>
    
      <div class="search" >
        <i class="bx bx-search" />
        <input type="text" class="hide" placeholder="Quick Search ..." />
      </div>
    
      <div class="sidebar-links" >
        <ul>
          <div class="active-tab" />
          <li class="tooltip-element" data-tooltip="0">
            <a href="/my/edit" class="active" data-active="0">
              <div class="icon">
                <i class='bx bx-edit' ></i>
                <i class='bx bxs-edit' ></i>
              </div>
              <span class="link hide">Edit</span>
            </a>
          </li>
          <li class="tooltip-element" data-tooltip="1">
            <a href="#" data-active="1">
              <div class="icon">
                <i class='bx bx-purchase-tag' ></i>
                <i class='bx bxs-purchase-tag' ></i>
              </div>
              <span class="link hide">Tag</span>
            </a>
          </li>
          <li class="tooltip-element" data-tooltip="2">
            <a href="#" data-active="2">
              <div class="icon">
                <i class='bx bx-archive' ></i>
                <i class='bx bxs-archive' ></i>
              </div>
              <span class="link hide">Archive</span>
            </a>
          </li>
          <li class="tooltip-element" data-tooltip="3">
            <a href="#" data-active="3">
              <div class="icon">
                <i class="bx bx-bar-chart-square" />
                <i class="bx bxs-bar-chart-square" />
              </div>
              <span class="link hide">Analytics</span>
            </a>
          </li>
          <div class="tooltip">
            <span class="show">Dashboard</span>
            <span>Projects</span>
            <span>Messages</span>
            <span>Analytics</span>
          </div>
        </ul>
    
        <h4 class="hide" >More</h4>
        
        <ul>
          <li class="tooltip-element" data-tooltip="0">
            <a href="#" data-active="4">
              <div class="icon">
                <i class='bx bx-directions'></i>
                <i class='bx bxs-directions'></i>
              </div>
              <span class="link hide">Community</span>
            </a>
          </li>
          <li class="tooltip-element" data-tooltip="1">
            <a href="/my/help" data-active="5">
              <div class="icon">
                <i class="bx bx-help-circle" />
                <i class="bx bxs-help-circle" />
              </div>
              <span class="link hide">Help</span>
            </a>
          </li>
          <li class="tooltip-element" data-tooltip="2">
            <a href="/my/settings" data-active="6">
              <div class="icon">
                <i class="bx bx-cog" />
                <i class="bx bxs-cog" />
              </div>
              <span class="link hide">Settings</span>
            </a>
          </li>
          <div class="tooltip">
            <span class="show">Community</span>
            <span>Help</span>
            <span>Settings</span>
          </div>
        </ul>
      </div>
    
      <div class="sidebar-footer">
        <a href="#" class="account tooltip-element" data-tooltip="0">
          <i class="bx bx-user" />
        </a>
        <div class="admin-user tooltip-element" data-tooltip="1">
          <div class="admin-profile hide">
            <img src="/avatar.png" alt="" />
            <div class="admin-info">
              <h3>Ryan Guan</h3>
              <h5>Admin</h5>
            </div>
          </div>
          <a href="#" class="log-out">
            <i class="bx bx-log-out" />
          </a>
        </div>
        <div class="tooltip">
          <span class="show">John Doe</span>
          <span>Logout</span>
        </div>
      </div>
    </nav>
  </div>
  
  <slot />
  