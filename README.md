# mon-dropdown

MonDropdown a feature-rich dropdown Vue2 component. It focuses on bringing the best of Vue's features to achieve common &amp; advanced behavior patterns while giving you the freedom to style the component to your liking. Built-to-work with <a href="https://tailwindcss.com/">TailwindCSS</a>.

![mon-dropdown-gif](https://github.com/irfancoder/mon-dropdown/blob/master/asset/mon-dropdown.gif)

[Demo](https://jsfiddle.net/irfancoder/0L1o23s8/110/)

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

| Props                 | Type          | Default                       |
| -------------         |-------------  | :-----------------:           |
| label                 | string        |                               |
| labelClass            | string        |                               |
| contentClass          | string        | 'mon-dropdown-content'        |
| enterActiveClass      | string        | 'mon-dropdown-enter-active'   |
| enterClass            | string        | 'mon-dropdown-enter'          |
| enterToClass          | string        | 'mon-dropdown-enter-to        |
| leaveActiveClass      | string        | 'mon-dropdown-leave-active'   |
| leaveClass            | string        | 'mon-dropdown-leave'          |
| leaveToClass          | string        | 'mon-dropdown-leave-to'       |
| anchor                | boolean       | false                         |
| dropUp                | boolean       | false                         |
| persistent            | boolean       | false                         |
| disableClickAway      | boolean       | false                         |
| disableEsc            | boolean       | false                         |
| openOnMount           | boolean       | false                         |

2. Combinations of Slots & Props
```
<!-- Basic Dropdown -->
props: 
* label
* labelClass
* anchor
* dropUp
* persistent
* disableClickAway
* disableEsc
* openOnMount 
  <mon-dropdown [...props]>
      <template #content="{ close, toggle }">...</template>
  </mon-dropdown>
  
<!-- Custom Trigger -->
props: 
* anchor
* dropUp
* persistent
* disableClickAway
* disableEsc
* openOnMount 

  <mon-dropdown [...props]>
    <template #trigger="{ toggle, open }">...</template>
    <template #content="{ toggle, close }">...</template>
  </mon-dropdown>
  
```

3. Lifecycle Hooks

| Hooks                 | Type          |
| -------------         |-------------  |
| before-open           | function      |
| after-open            | function      |
| before-close          | function      |
| after-close           | function      |

Check the [Demo](https://jsfiddle.net/irfancoder/0L1o23s8/110/) on how to use dropdown lifecycle hooks

4. Handling Dropdown Behavior outside Usual Scope

There will be times, you will find yourselves needing to trigger dropdown behaviors outside of the normal scope (eg. clicking a button). MonDropdown provides three (3) internal functions that can be accessed through Vue's `ref="..." & $refs`.

The three (3) functions are:

- toggleDropdown()
- openDropdown()
- closeDropdown()

Check the [Demo](https://jsfiddle.net/irfancoder/0L1o23s8/110/) on how to use dropdown's internal functions

<!-- LICENSE -->
## License
<a href="https://opensource.org/licenses/mit-license.php" target="_blank">MIT License</a>

<!-- CONTACT -->
## Contact

Irfan Ismail - [@irfancoder](https://twitter.com/irfancoder) - irfan.ismail96@gmail.com
