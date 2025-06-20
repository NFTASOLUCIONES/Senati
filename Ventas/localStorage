// ...existing code...

// Cambia estas líneas:
let products = [];
let salesData = [];

// Cargar productos y ventas desde el backend
async function loadData() {
    const productsRes = await fetch('http://localhost:3000/products');
    products = await productsRes.json();
    const salesRes = await fetch('http://localhost:3000/sales');
    salesData = await salesRes.json();
    renderProducts();
}
loadData();

// Guardar productos en el backend
async function saveProducts() {
    await fetch('http://localhost:3000/products', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(products)
    });
}

// Guardar ventas en el backend
async function saveSales() {
    await fetch('http://localhost:3000/sales', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(salesData)
    });
}

// Modifica las funciones que cambian productos/ventas:
productForm.addEventListener('submit', async (event) => {
    // ...existing code...
    products.push(newProduct);
    await saveProducts();
    renderProducts();
    productForm.reset();
});

window.updateQuantity = async (index, change) => {
    products[index].quantity += change;
    if (products[index].quantity < 0) products[index].quantity = 0;
    await saveProducts();
    renderProducts();
};

window.deleteProduct = async (index) => {
    products.splice(index, 1);
    await saveProducts();
    renderProducts();
};

window.recordSale = async (index) => {
    // ...existing code...
    salesData.push(sale);
    await saveSales();
    alert(`Venta registrada: ${product.name}, Total: S/${sale.total.toFixed(2)}`);
};

// ...existing code...