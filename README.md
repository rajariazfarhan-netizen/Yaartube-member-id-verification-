<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Yaar Tube Member Verification</title>
<style>
  body { font-family: Arial, sans-serif; background: #f5f5f5; margin:0; padding:0; }
  header { background: #1e7d3b; color:white; padding: 20px; text-align:center; }
  .container { max-width:900px; margin:20px auto; background:white; padding:20px; border-radius:10px; box-shadow:0 0 10px rgba(0,0,0,0.1); }
  table { width:100%; border-collapse: collapse; }
  th, td { padding:10px; text-align:left; border-bottom:1px solid #ddd; }
  th { background:#1e7d3b; color:white; }
  .active { color:green; font-weight:bold; }
  .removed { color:red; font-weight:bold; }
  img { width:50px; height:50px; border-radius:50%; object-fit:cover; }
  input[type="text"] { padding:8px; width:100%; margin-bottom:10px; border-radius:5px; border:1px solid #ccc; }
</style>
</head>
<body>

<header>
  <h1>Yaar Tube Member Verification</h1>
</header>

<div class="container">
  <input type="text" id="searchBox" placeholder="Search by Member ID or Name..." onkeyup="filterMembers()">

  <table id="memberTable">
    <thead>
      <tr>
        <th>Photo</th>
        <th>Name</th>
        <th>Member ID</th>
        <th>Status</th>
      </tr>
    </thead>
    <tbody>
      <!-- Members will be populated here -->
    </tbody>
  </table>
</div>

<script>
// Sample data: Replace with actual member data
const members = [
  {id:"YT001", name:"Ali Khan", photo:"https://via.placeholder.com/50", status:"ACTIVE"},
  {id:"YT002", name:"Sara Ahmed", photo:"https://via.placeholder.com/50", status:"REMOVED"},
  {id:"YT003", name:"Omar Rizvi", photo:"https://via.placeholder.com/50", status:"ACTIVE"},
  // Add more members here
];

const tbody = document.querySelector("#memberTable tbody");

// Function to display members
function displayMembers(list) {
  tbody.innerHTML = "";
  list.forEach(member => {
    const row = document.createElement("tr");
    row.innerHTML = `
      <td><img src="${member.photo}" alt="${member.name}"></td>
      <td>${member.name}</td>
      <td>${member.id}</td>
      <td class="${member.status.toLowerCase()}">${member.status}</td>
    `;
    tbody.appendChild(row);
  });
}

// Function to filter members by ID or Name
function filterMembers() {
  const query = document.getElementById("searchBox").value.toLowerCase();
  const filtered = members.filter(m => 
    m.id.toLowerCase().includes(query) || m.name.toLowerCase().includes(query)
  );
  displayMembers(filtered);
}

// Initial display
displayMembers(members);
</script>

</body>
</html>
