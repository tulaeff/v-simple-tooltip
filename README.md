## Installation

```
npm install --save v-simple-tooltip
```

## Usage

```
<template>
  <table>
    <tr>
      <td @mouseover="show_tooltip = true"
          @mouseleave="show_tooltip = false">
            
        Some text

        <VSimpleTooltip
          v-if="show_tooltip"
          :content="tooltip_content"
          :style="{
            'text-align': 'center',
            'color': 'red'
          }"
        ></VSimpleTooltip>
      </td>
    </tr>
  </table>
</template>

<script>
  import VSimpleTooltip from 'v-simple-tooltip';
		
  export default {
    name: 'SomeExampleComponent',
    components: {VSimpleTooltip},
    data() {
      return {
        show_tooltip: false,
        tooltip_content: '<b>HTML-compatible content</b><br>of tooltip'
      }
    }
  }
</script>
```

---

LICENCE MIT - Created by Sergey Tulaeff (@tulaeff)