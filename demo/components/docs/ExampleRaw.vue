<template>
  <vsm-menu
    :menu="menu"
    element="header"
    handler="hover"
    align="center"
    :screen-offset="10"
    :dropdown-offset="0"
    @open-dropdown="onOpenDropdown"
    @close-dropdown="onCloseDropdown"
  >
    <template #default="{ item }">
      <!--Dropdown content of each menu item with a "dropdown" property-->
      <!--You can replace it with a separate component if each menu item has its own style-->
      <!--Necessarily need to have at least one element within the slot-->
      <!--An alternate background will be applied from the 2nd element-->
      <div style="width: 300px; padding: 30px">
        Header: {{ item }}
      </div>
      <div style="padding: 30px">
        Second element
      </div>
    </template>
    <template #before-nav>
      <!--Image or svg of website logo-->
      <li style="width: 50px; height: 50px">
        <img
          src="https://vuejs.org/images/logo.png"
          alt="My Logo"
        >
      </li>
    </template>
    <template #title="data">
      <!--Display menu items through slots-->
      {{ data.item.title }}
    </template>
    <template #after-nav>
      <!--Mobile Burger, buttons, etc-->
      <li class="vsm-mob-hide">
        <button>My Button</button>
      </li>
      <!--Set "display: block" for the .vsm-mob-show class to display content-->
      <vsm-mob>Mobile Content</vsm-mob>
    </template>
  </vsm-menu>
</template>

<script>
/* eslint-disable */
/*
 * Inside #after-nav and #before-nav it is recommended to use
 * to maintain the correct HTML structure:
 *   <li><!--Content--></li>
 */

export default {
  data() {
    return {
      menu: [
        {
          // display menu item (can be overridden with title slot)
          title: 'News',
          // this element now has dropdown content
          dropdown: 'news',
          // don't want a button element? Pass HTMLElement or global component
          // (pass only as a string, component must be globally accessible)
          element: 'span', // router-link
          // offset the position of the dropdown menu
          align: 'center',
          // menu item can accept all attributes
          attributes: {
            // I want more classes! No problem
            // string, array, object, not matter
            class: ['my-class1', { 'my-class2': true }],
            // Custom attributes
            'data-big': 'yes'
          },
          // add some events?
          listeners: {
            // all possible native events
            mouseover: (evt) => {
              console.log('news hover', evt)
            }
          },
          // just extra properties in the object
          new_section: false,
        },
        {
          title: 'External Link',
          attributes: {
            href: 'https://github.com/Alexeykhr/vue-stripe-menu',
            target: '_blank'
          }
        }
        // ...
      ]
    }
  },
  methods: {
    onOpenDropdown() {
      console.log('onOpenDropdown')
    },
    onCloseDropdown() {
      console.log('onCloseDropdown')
    }
  }
}
</script>
