<template>
  <table>
    <thead>
    <tr>
      <th>#</th>
      <th>Сумма</th>
      <th>Дата</th>
      <th>Категория</th>
      <th>Тип</th>
      <th>Открыть</th>
    </tr>
    </thead>

    <tbody>
      <tr v-for="record, idx in records" :key="record.id" >
        <td>{{ idx + 1 }}</td>
        <td>{{ record.amount }}</td>
        <td>{{ record.date }}</td>
        <td>{{ record.categoryName }}</td>
        <td>
          <span
            class="white-text badge"
            :class="record.typeClass"
          >{{ record.typeText }}</span>
        </td>
        <td>
          <button
            class="btn-small btn"
            @click="$router.push('/detail/' + record.id)"
            title="Посмотреть запись"
          >
            <i class="material-icons">open_in_new</i>
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: {
    records: {
      type: Array,
      required: true
    }
  }
}
</script>
