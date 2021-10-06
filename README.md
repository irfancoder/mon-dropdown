# mon-dropdown

MonModal a feature-rich dropdown Vue2 component. It focuses on bringing the best of Vue's features to achieve common &amp; advanced behavior patterns while giving you the freedom to style the component to your liking. Built-to-work with <a href="https://tailwindcss.com/">TailwindCSS</a>.

![mon-dropdown-gif](https://github.com/irfancoder/mon-dropdown/blob/master/asset/mon-dropdown.gif)

[Demo](https://jsfiddle.net/irfancoder/6rcuwbq0/289/)
<!-- GETTING STARTED -->
## Getting Started 

```
// npm
npm i @irfanismail/mon-dropdown

// yarn
yarn add @irfanismail/mon-dropdown
```


<!-- USAGE EXAMPLES -->
## Usage 

1. Table of Props

| Props                 | Type          | Default               |
| -------------         |-------------  | :-----------------:   |
| title                 | string        |                       |
| label                 | string        |                       |
| titleClass            | string        | 'mon-dropdown-title'     |
| labelClass            | string        |                       |
| backdropClass         | string        | 'mon-dropdown'           |
| dropdownClass            | string        | 'mon-dropdown-container' |
| headerClass           | string        | 'mon-dropdown-header'    |
| bodyClass             | string        | 'mon-dropdown-body'      |
| footerClass           | string        | 'mon-dropdown-footer'    |
| persistent            | boolean       | false                 |
| disableClickAway      | boolean       | false                 |
| disableEsc            | boolean       | false                 |
| openOnMount           | boolean       | false                 |

2. Combinations of Slots & Props
```
<!-- Basic Modal -->
props: 
* label 
  <mon-dropdown [...props]>
      <template #body>...</template>
      <template #footer="{ close }">...</template>
  </mon-dropdown>
  
<!-- Custom Header & Content -->
props: 
* label 
  <mon-dropdown [...props]>
    <template #header="{ close }">...</template>
    <template #custom="{ open, close }">...</template>
  </mon-dropdown>

<!-- Custom Trigger -->
props: 
 * title
  <mon-dropdown [...props]>
    <template #trigger="{ open }"></template>
    <template #body>...</template>
  </mon-dropdown>

  
```
3. Lifecycle Hooks

| Hooks                 | Type          |
| -------------         |-------------  |
| before-open           | function      |
| after-open            | function      |
| before-close          | function      |
| after-close           | function      |

Check the [Demo](https://jsfiddle.net/irfancoder/6rcuwbq0/289/) on how to use dropdown lifecycle hooks

5. Handling Modal Behavior outside Usual Scope

There will be times, you will find yourselves needing to trigger dropdown behaviors outside of the normal scope (eg. clicking a button). MonModal provides two (2) internal functions that can be accessed through Vue's `ref="..." & $refs`.

The two functions are:

- openModal()
- closeModal()

Check the [Demo](https://jsfiddle.net/irfancoder/6rcuwbq0/289/) on how to use dropdown's internal functions


<!-- ROADMAP -->
## Roadmap 

TODO: 
- Improve Base styling
- Add Base Transition Animation
- Allow Custom Transition Animation

<!-- LICENSE -->
## License


<!-- CONTACT -->
## Contact

Irfan Ismail - [@irfancoder](https://twitter.com/irfancoder) - irfan.ismail96@gmail.com
