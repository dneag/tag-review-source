<!-- A dropdown list created using html 'select' and 'option' elements.  The contents of the list are populated 
     by a parent component.  Selections from the list are sent back to the parent -->
     
<template>
  <select :id="ddID" @change="sendSelection" class="h-6 rounded-r-lg border-2"></select>
</template>

<script>

export default {
  props: ['ddID'],
  methods: {

    // setList() is called from parent
    setList(listFromParent) {
      
      for (var item of listFromParent) {

        var elem = document.createElement("option");
        elem.textContent = item.name;
        elem.value = item.name;
        document.getElementById(this.ddID).appendChild(elem);
      }
    },
    async sendSelection() {

      let item = document.getElementById(this.ddID).value;
      this.$emit('itemSelected', item);
    }
  }
}

</script>

