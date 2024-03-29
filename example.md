---
theme: ./
layout: cover
background: #FFF
top-left-img: ./public/images/nju.png
---

# This is A Test Title

Presented by Qin-Cheng Zheng

<style>
  .slidev-layout.cover h1 {
    @apply text-6xl font-500;
  }
</style>

---

# Outline

<div v-click>

- Background
- Setting and Notations
- Method
- Theory
- Experiment
- Summary

</div>

<style>
  .slidev-layout {
    .slidev-vclick-target {
      transition: all 500ms ease;
    }

    .slidev-vclick-hidden {
      transform: translate(0, 100%);
    }
  }
</style>

---

# Definition and Theorem

<div v-click class="theorem1">
  <ulli>Definition of product distribution</ulli>
  <Theorem type="Definition">
    Let <IE>p</IE> and <IE>f</IE> be a product distribution and a mapping from <IE>\mathcal{X}</IE> to <IE>\mathcal{Y} = \{0, 1\}</IE>, respectively.
    We say a distribution <IE>\textbf{p}</IE> is a product disribution if we have
    <E>
      \mathbf{p} = \prod_{i = 1}^{d} \mathbf{p}^{(i)} \ ,
    </E>
    where <IE>\mathbf{p}^{(i)}</IE> is the marginal distribution on the <IE>i</IE> dimension.
  </Theorem>
</div>

<div v-click class="theorem2">
  <ulli>Properties of product distribution</ulli>
  <Theorem type="Theorem">
    Every product distribution is a good distribution.
  </Theorem>
</div>

<g-canvas arrow-fill="black" :debug="true"></g-canvas>

<reference :total="3" :number="1" authors="B.-C. A and E.-F. D" title="This is a Test Title" source="ICML 19">
</reference>
<reference :total="3" :number="2" authors="B.-C. A and E.-F. D" title="This is a Test Title" source="IJCAI 20">
</reference>
<reference :total="3" :number="3" authors="B.-C. A and E.-F. D" title="This is a Test Title" source="AAAI 21">
</reference>

<style>
  .slidev-vclick-target {
    transition: all 500ms ease;
  }
  .slidev-vclick-hidden {
    transform: scale(.95);
  }
</style>

---
layout: section
---

# Setting and Notations

---
layout: two-cols
---

# Grid

::left::
- This shows on the left

<svg class="mt-3" viewBox="0 0 100 80">
  <animate-path
    v-click
    class="!duration-1000 fill-none stroke-black"
    d="M20 40
        a20 20 0 0 1 20 -20
        a20 20 0 0 1 20 20
        a20 20 0 0 1 -20 20
        a20 20 0 0 1 -20 -20"
  />
</svg>

::right::
- This shows on the right

<svg class="mt-3" viewBox="0 0 100 80">
  <animate-path
    v-click
    class="!duration-1000 fill-none stroke-black stroke-cap-round"
    d="M20 20 h40 v40 h-40 v-40 Z"
  />
</svg>

---

# Code

```ts {all|2|1-6|all}
interface User {
  id: number
  firstName: string
  lastName: string
  role: string
}

function updateUser(id: number, update: Partial<User>) {
  const user = getUser(id)
  const newUser = {...user, ...update}  
  saveUser(id, newUser)
}
```

---
layout: center
class: "text-center"
---

# Learn More

[Documentations](https://sli.dev) / [GitHub Repo](https://github.com/slidevjs/slidev)

---

# H1
## H2
### H3
#### H4
##### H5
###### H6
