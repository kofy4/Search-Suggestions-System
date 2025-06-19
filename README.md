class SearchSuggestionSystem {
  constructor(products) {
    // Sort the products lexicographically
    this.products = products.sort();
  }

  getSuggestions(searchWord) {
    let result = [];
    let prefix = "";

    for (let char of searchWord) {
      prefix += char;
      let suggestions = [];

      for (let product of this.products) {
        if (product.startsWith(prefix)) {
          suggestions.push(product);
          if (suggestions.length === 3) break; // Only take up to 3
        }
      }

      result.push(suggestions);
    }

    return result;
  }
}
