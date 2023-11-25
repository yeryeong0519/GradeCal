<!-- src/components/Table.vue -->
<template>
  <div>
    <div class="button-container">
      <button @click="addRow">추가</button>
      <button @click="deleteRow">삭제</button>
      <button @click="saveData">저장</button>
    </div>
    <table class="sky-blue-table">
      <thead>
      <tr>
        <th v-for="header in headers" :key="header">
          {{ header }}
        </th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(row, rowIndex) in rows" :key="rowIndex">
        <td
            v-for="(cell, cellIndex) in row"
            :key="cellIndex"
            :colspan="cell.colspan || 1"
        >
          {{ typeof cell === 'object' ? cell.text : (cell.value !== undefined ? cell.value : '') }}
        </td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      headers: ['이수', '필수', '과목명', '학점', '출석점수', '과제점수', '중간고사', '기말고사', '총점', '평균', '성적'],
      rows: [
        [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11],
        [{ text: '합계', colspan: 3 }, 59, 60, 61, 62, 63, 64, 65, 66],
      ],
    };
  },
  methods: {
    addRow() {
      const newRow = Array.from({ length: this.headers.length }, (_, index) => {
        if (index === 0) {
          // 이수 행
          return { type: 'select', options: ['교양', '전공'], value: '' };
        } else if (index === 1) {
          // 필수 행
          return { type: 'select', options: ['필수', '선택'], value: '' };
        } else {
          return '';
        }
      });
      this.rows.splice(this.rows.length - 1, 0, newRow);
    },
    deleteRow() {
      if (this.rows.length > 1) {
        this.rows.splice(this.rows.length - 2, 1);
      }
    },
    saveData() {
      // TODO: 데이터 저장 로직을 작성하세요.
    },
  },
};
</script>

<style scoped>
.sky-blue-table {
  background-color: skyblue;
  width: 100%;
  border-collapse: collapse;
}

.sky-blue-table th, .sky-blue-table td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: center;
}

.button-container {
  margin-bottom: 10px;
  text-align: right; /* 우측 정렬 스타일 추가 */
}

.button-container button {
  margin-left: 10px; /* 버튼 사이의 간격 조절을 위한 스타일 추가 */
}
</style>
