---
layout: post
title:  "Form Typeahead using the new Fetch API"
date: 2016-12-20 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 2
feature_image: macbook
show_related_posts: false
square_related: recommend-wolf
---
<style>
button, input, optgroup, select, textarea {
    margin: 0;
    font: inherit;
    color: inherit;
    width: 500px;
    height: 60px;
}
</style>
Pretty simple demo: Start typing into the form box. Try "Boston" or "Massachusetts" - This was built using the new HTML Fetch API. It's really cool to be able to do this all client side with no need for anything else. [You can learn more about Fetch over on David Walsh's blog.](https://davidwalsh.name/fetch "Fetch")

<body>

  <form class="search-form">
    <input type="text" class="search" placeholder="Start typing City or State name here" autofocus>
    <ul class="suggestions">
      <li>Filter for a city</li>
      <li>or a state</li>
    </ul>
  </form>
<script>
const endpoint = 'https://gist.githubusercontent.com/Miserlou/c5cd8364bf9b2420bb29/raw/2bf258763cdddd704f8ffd3ea9a3e81d25e2c6f6/cities.json';

const cities = [];
fetch(endpoint)
  .then(blob => blob.json())
  .then(data => cities.push(...data));

function findMatches(wordToMatch, cities) {
  return cities.filter(place => {
    const regex = new RegExp(wordToMatch, 'gi');
    return place.city.match(regex) || place.state.match(regex)
  });
}

function numberWithCommas(x) {
  return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
}

function displayMatches() {
  const matchArray = findMatches(this.value, cities);
  const html = matchArray.map(place => {
    const regex = new RegExp(this.value, 'gi');
    const cityName = place.city.replace(regex, `<span class="hl">${this.value}</span>`);
    const stateName = place.state.replace(regex, `<span class="hl">${this.value}</span>`);
    return `
      <li>
        <span class="name">${cityName}, ${stateName}</span>
        <span class="population">Population: ${numberWithCommas(place.population)}</span>
      </li>
    `;
  }).join('');
  suggestions.innerHTML = html;
}

const searchInput = document.querySelector('.search');
const suggestions = document.querySelector('.suggestions');

searchInput.addEventListener('change', displayMatches);
searchInput.addEventListener('keyup', displayMatches);

</script>
</body>
