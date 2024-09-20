<!DOCTYPE html>
<html>
<head>
  <title>Pagination Component</title>
  <style>
    .pagination {
      display: flex;
      justify-content: center;
      margin-top: 20px;
    }

    .page-item {
      margin: 0 5px;
      padding: 8px 12px;
      border: 1px solid #ccc;
      border-radius: 5px;
      cursor: pointer;
    }

    .page-item.active {
      background-color: #4caf50;
      color: white;
    }
  </style>
</head>
<body>
  <div id="data-container">
    <!-- Data will be displayed here -->
  </div>

  <div class="pagination" id="pagination-container"></div>

  <script>
    // Sample data (replace with your actual data)
    const data = [
      { id: 1, name: "Item 1" },
      { id: 2, name: "Item 2" },
      { id: 3, name: "Item 3" },
      { id: 4, name: "Item 4" },
      { id: 5, name: "Item 5" },
      { id: 6, name: "Item 6" },
      { id: 7, name: "Item 7" },
      { id: 8, name: "Item 8" },
      { id: 9, name: "Item 9" },
      { id: 10, name: "Item 10" }
    ];

    const dataContainer = document.getElementById('data-container');
    const paginationContainer = document.getElementById('pagination-container');

    // Items per page
    const itemsPerPage = 3;

    // Function to display data on the current page
    function displayData(currentPage) {
      dataContainer.innerHTML = ''; // Clear previous data

      const startIndex = (currentPage - 1) * itemsPerPage;
      const endIndex = startIndex + itemsPerPage;

      for (let i = startIndex; i < endIndex && i < data.length; i++) {
        const item = data[i];
        const itemElement = document.createElement('div');
        itemElement.textContent = ID: ${item.id}, Name: ${item.name};
        dataContainer.appendChild(itemElement);
      }
    }

    // Function to create pagination buttons
    function createPagination() {
      const totalPages = Math.ceil(data.length / itemsPerPage);

      // Create pagination buttons
      paginationContainer.innerHTML = ''; // Clear previous pagination
      for (let i = 1; i <= totalPages; i++) {
        const pageItem = document.createElement('div');
        pageItem.classList.add('page-item');
        pageItem.textContent = i;

        // Add event listener for clicking on pagination buttons
        pageItem.addEventListener('click', () => {
          displayData(i);
          // Update the active page class
          const activePageItem = paginationContainer.querySelector('.active');
          if (activePageItem) {
            activePageItem.classList.remove('active');
          }
          pageItem.classList.add('active');
        });

        paginationContainer.appendChild(pageItem);
      }

      // Mark the first page as active initially
      paginationContainer.children[0].classList.add('active');
    }

    // Initial display of data and pagination
    displayData(1); // Display the first page
    createPagination();
  </script>
</body>
</html>
