<template>
  <div class="container">
    <b-table hover :items="items" :fields="fields"></b-table>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        fields: [
          {
            key: 'platform',
            label: 'Платформа',
            sortable: true
          },
          {
            key: 'maker',
            label: 'Производитель',
            sortable: true
          },
          {
            key: 'devices',
            label: 'Всего устройств',
            sortable: true
          },
          {
            key: 'active',
            label: 'Активных',
            sortable: true
          },
          {
            key: 'activeN',
            label: 'Активных (not inUse)',
            sortable: true
          },
          {
            key: 'notActive',
            label: 'Неактивных',
            sortable: true
          },
          {
            key: 'notInterviewed',
            label: 'Не опрошенных',
            sortable: true
          }
        ],
        items: [
          { isActive: true, platform: 'c1', maker: 'A', devices: 30, active: 13, activeN: 124, notActive: 151, notInterviewed: 1241},
          { isActive: true, platform: 'c2', maker: 'B', devices: 12, active: 1254, activeN: 123, notActive: 1111, notInterviewed: 151},
          { isActive: true, platform: 'c3', maker: 'C', devices: 123, active: 14, activeN: 124, notActive: 1511, notInterviewed: 1},
          { isActive: true, platform: 'c3', maker: 'D', devices: 213, active: 153, activeN: 241, notActive: 163, notInterviewed: 14},
          { isActive: true, platform: 'c4', maker: 'E', devices: 21, active: 25, activeN: 21, notActive: 16, notInterviewed: 124},
          { isActive: true, platform: 'c5', maker: 'F', devices: 11, active: 1267, activeN: 712, notActive: 3561, notInterviewed: 14}
        ]
      }
    }
  }
</script>

<style scoped>
.container {
    margin-top: 100px;
}
</style>