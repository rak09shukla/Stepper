<template>
  <div class="table-parent-component">
    <table class="preview-table">
      <caption></caption>
      <thead>
        <tr>
          <th
            id="content-header"
            v-for="(header,index) in content.headers"
            :key="`header-${index}`"
          >{{header}}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(rowValue,index) in content.tableValues" :key="`rowValue-${index}`">
          <td v-for="(independentRowData,index) in rowValue" :key="`independentRowData-${index}`">
            <span v-if="independentRowData.type === 'checkbox'">
              <label class="form-checkbox">
                <input type="checkbox" />
                <em class="form-icon"></em>
              </label>
            </span>
            <span v-else-if="independentRowData.type === 'text'">{{independentRowData.value}}</span>
            <span v-else-if="independentRowData.type === 'dropDown'">
              <select>
                <option
                  v-for="(dropdownList,index) in  independentRowData.value"
                  :key="`dropdownList-${index}`"
                >{{dropdownList}}</option>
              </select>
            </span>
            <span v-else>No Data to show</span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  props: ["content"]
};
</script>
<style>
</style>