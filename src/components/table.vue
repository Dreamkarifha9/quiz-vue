<template lang="">
  <div>
    <table>
      <thead>
        <tr>
          <th>Product</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in output" :key="item">
          <td>{{ item }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
const input = {
  "products": [
    {
      "variants": ["souffle", "cake", "ice-cream"]
    },
    {
      "variants": ["cherry", "choco"]
    },
    {
      "variants": ["XL"]
    }
  ]
};

const output = [];

// Nested loops to generate combinations
const maxLengthProduct = input.products[0].variants.length
const maxLengthVariant = input.products[1].variants.length
const maxLengthSize = input.products[2].variants.length
console.log(input.products[0].variants.length)
for (let p = 0; p < maxLengthProduct; p++) {
  for (let v = 0; v < maxLengthVariant; v++) {
    for (let s = 0; s < maxLengthSize; s++) {
      for (let product of input.products[0].variants) {
        const strCompare = `${product} ${input.products[1].variants[v]} ${input.products[2].variants[s]}`
        if (output.includes(strCompare)) {
          continue;
        }
        output.push(strCompare)
      }
    }
  }
}

export default {
  data() {
    return {
      output
    }
  }
}
</script>
<style lang="">
  
</style>