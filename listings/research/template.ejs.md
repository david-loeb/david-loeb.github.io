```{=html}
<% for (const item of items) { %>
  <div class="list">
    <div class="research-card">

      <div class="research-title research-content">
        <% if (item.url) { %>
          <a href="<%- item.url %>" target="_blank"><%- item.title %></a>
        <% } else { %>
          <%- item.title %>
        <% } %>
      </div>

      <% if (item.authors) { %>
        <p class="research-authors research-content"><%= item.authors %></p>
      <% } %>

      <% if (item.publication && item.institution && item.year) { %>
        <p class="research-pub research-content">
            <%- item.year %>, <i><%- item.publication %></i>, <%- item.institution %>
        </p>
      <% } else if (item.publication && item.year) { %>
        <p class="research-pub research-content"><%- item.year %>, <i><%- item.publication %></i></p>
      <% } else if (item.institution && item.year) { %>
        <p class="research-pub research-content"><%- item.year %>, <%- item.institution %></p>
      <% } else if (item.year) { %>
        <p class="research-pub research-content"><%- item.year %></p>
      <% } %>

      <% if (item.press) { %>
        <p class="research-press research-content"><i>
          Press: <% for (let i = 0; i < item.press.length; i++) { 
            if (i === item.press.length - 1) { %>
              <a href="<%- item.press[i].url %>" target="_blank"><%- item.press[i].outlet %></a>
            <% } else { %>
              <a href="<%- item.press[i].url %>" target="_blank"><%- item.press[i].outlet %></a>, 
            <% } %>
          <% } %>
        </i></p>
      <% } %>

      <% if (item.links) { %>
        <div class="research-links">
          <% for (const link of item.links) { %>
            <a class="research-link" href="<%- link.url %>" target="_blank">
              <i class="<%- link.icon %>"></i> <%= link.name %>
            </a>
          <% } %>
        </div>
      <% } else { %>
        <div class="research-links research-links-empty">&nbsp;</div>
      <% } %>

    </div>
  </div>
<% } %>
```