<template>
  <ul class="wrapper">
    <li v-for="item in list" :key="'item'+item.title">
      <!-- font awesome icon with a rotating animation -->
      <div class="iconos">
        <a href="#"><i class="fa fa-edit icon" style="margin-right: 10px" /></a><i class="fa fa-user icon" style="margin-right: 10px" />
        <i
          class="fas fa-chevron-circle-right"
          :class="{'open':item.open}"
        />
      </div>
      <!-- The list title with the click event for toggling the open status -->
      <div class="title" @click="item.open = !item.open">
        {{ item.title }}
      </div>
      <!-- renders the ListItem Component for each list element -->
      <ListItem :list="item" />
    </li>
  </ul>
</template>

<script>
import ListItem from './ListItem'

export default {
  components: {
    ListItem
  },
  data: () => {
    return {
      /*
          Some test data for the accordion,
          you can use this for a sidebar navigation or simply as a faq list, for example
        */
      list: [
        {
          title: 'Roles',
          open: false,
          sublist: [
            {
              title: 'administrador',
              open: false,
              sublist: [
                {
                  title: 'crear',
                  open: false,
                  sublist: [
                    {
                      title: 'archivos'
                    }
                  ]
                },
                {
                  title: 'editar'
                },
                {
                  title: 'borrar'
                }
              ]
            },
            {
              title: 'SCSS'
            },
            {
              title: 'JavaScript'
            },
            {
              title: 'Webpack'
            }
          ]
        },
        {
          title: 'mas..',
          open: false,
          sublist: [
            {
              title: 'Transitions'
            },
            {
              title: 'Course A'
            }
          ]
        },
        {
          title: 'mas2..',
          open: false,
          sublist: [
            {
              title: '2017'
            },
            {
              title: '2018'
            },
            {
              title: '2019'
            }
          ]
        },
        {
          title: 'mas3...',
          open: false,
          sublist: [
            {
              title: 'GitHub'
            },
            {
              title: 'YouTube'
            },
            {
              title: 'Dev.to'
            }
          ]
        },
        {
          title: 'mas4...',
          open: false,
          sublist: [
            {
              title: 'Article A'
            },
            {
              title: 'Article B'
            }
          ]
        }
      ]
    }
  }
}
</script>

<style>
  .wrapper {
    list-style: none;
    background-color: #fefefe;
    box-shadow: 0 2px rgba(0, 0, 0, 0.15);
    border-radius: 4px;
    overflow: hidden;
  }
  .wrapper li {
      position: relative;
      color: #555;
      border-top: 1px solid #dedede;
      cursor: pointer;
    }
    .wrapper li:hover {
        color: #4f7351;
        background-color: #DFEEE0;
      }
    .wrapper li .title {
        padding: 10px 0;
      }
      .wrapper li .iconos {
        position: absolute;
        top: 14px;
        right: 10px;
        transition: transform .5s ease-in-out;
        z-index: 1000;
      }
      .wrapper li .open {
          transform: rotateZ(90deg);
        }
</style>
