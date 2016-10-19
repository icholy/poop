POOP
---

> A crappy markup language

[@adam12](https://github.com/adam12) gave a talk about [Tachyons](http://tachyons.io/) and there was a lot contention.
In essense, they're nicer and more performant inline styles.
Almost every CSS guide/book will tell you not to use inline styles because "separation of concerns".

I use the [less](http://lesscss.org/) pre-processor which supports nesting rules.
What I realized is that my style structure are a reflection of my markup structure.
So why can't I remove that duplication?

Poop is an experimental markup language that embraces inline styling.
It rewrites and deduplicates each individual rule into a css class (kinda like Tachyons).

```
$ npm install
$ node build/poop.js examples/test.poop
```

```
div(id="test") {
  background-color: green;
  z-index: 9999;

  a(href="#") {
    > testing testing;
  }

  span {
    ul {
      background-color: red;
      z-index: 9999;

      li{}
      li{}
    }
    > hello world;
  }
}
```

``` css
.poop_A { background-color:green; }
.poop_B { z-index:9999; }
.poop_C { background-color:red; }

```

``` html
<div id="test" class="poop_A poop_B">
  <a href="#">
     testing testing
  </a>
  <span>
    <ul class="poop_C poop_B">
      <li>
      </li>
      <li>
      </li>
    </ul>
     hello world
  </span>
</div>

```
