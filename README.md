This project contains **Entity-Relationship (ER) Diagrams** for three systems:

1. **Library Management System**
2. **Restaurant Reservation System**
3. **Real Estate Listing System**

The ER diagrams are created using **Graphviz (Chen Notation)** and **Mermaid.js (Crow’s Foot Notation)** inside a **Quarto (`.qmd`) report**. The report also includes explanations of design choices and relationships.
Ensure you have **Quarto** and **Graphviz** installed on your system.

- **Install Quarto**: [Download here](https://quarto.org/docs/get-started/)
- **Install Graphviz**: [Download here](https://graphviz.gitlab.io/download/)
- **(Optional)** Install the **Live Server extension** in **VS Code** for quick HTML preview.

### **2️⃣ Render the Quarto Report**
Run the following command in the terminal:
```sh
quarto render er_diagram.qmd --to html
