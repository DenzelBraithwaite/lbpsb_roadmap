<script lang="ts">

</script>

<main class="relative pt-40">
  <div class="roadmap-wrapper p-2">
  <header class="flex justify-between items-center text-center h-1/6">
    <div class="flex">
      <p class="rounded-l-md p-2.5 bg-emerald-800 cursor-pointer hover:bg-emerald-700 text-white">&lt;</p>
      <p class="rounded-r-md p-2.5 bg-emerald-800 cursor-pointer hover:bg-emerald-700 text-white">&gt;</p>
    </div>
    <h1 class="text-4xl">Title</h1>
    <div class="flex">
      <p class="rounded-l-md p-2.5 bg-emerald-800 cursor-pointer hover:bg-emerald-700 text-white">Day</p>
      <p class="p-2.5 bg-emerald-800 cursor-pointer hover:bg-emerald-700 text-white">Week</p>
      <p class="rounded-r-md p-2.5 bg-emerald-800 cursor-pointer hover:bg-emerald-700 text-white">Month</p>
    </div>
  </header>
    <div class="table-wrapper">
      <table>
        <thead>
          <tr>
            <th>Employee</th>
            <th>Sun</th>
            <th>Mon</th>
            <th>Tue</th>
            <th>Wed</th>
            <th>Thu</th>
            <th>Fri</th>
            <th>Sat</th>
            <th>Sun</th>
            <th>Mon</th>
            <th>Tue</th>
            <th>Wed</th>
            <th>Thu</th>
            <th>Fri</th>
            <th>Sat</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th>Denzel1</th>
            <td>1</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
            <td>6</td>
            <td>7</td>
          </tr>
          <tr>
            <th>Denzel2</th>
            <td>1</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
            <td>6</td>
            <td>7</td>
          </tr>
          <tr>
            <th>Denzel3</th>
            <td>1</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
            <td>6</td>
            <td>7</td>
          </tr>
          <tr>
            <th>Denzel4</th>
            <td>1</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
            <td>6</td>
            <td>7</td>
          </tr>
          <tr>
            <th>Denzel5</th>
            <td>1</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
            <td>6</td>
            <td>7</td>
          </tr>
          <tr>
            <th>Denzel</th>
            <td>1</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
            <td>6</td>
            <td>7</td>
          </tr>
          <tr>
            <th>Denzel</th>
            <td>1</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
            <td>6</td>
            <td>7</td>
          </tr>
          <tr>
            <th>Denzel</th>
            <td>1</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
            <td>6</td>
            <td>7</td>
          </tr> 
        </tbody>
        <!-- <tfoot></tfoot> -->
      </table>
    </div>
  </div>
</main>

<style>
  .roadmap-wrapper {
    position: relative;
    border: 1px solid #36363625;
    box-shadow: 0px 2px 10px #0000001e;
    border-top: 4px solid #10B981;
    width: 90vw;
    height: 70vh;
    margin: 0 auto;
    padding-bottom: 50px;
  }

  .table-wrapper {
    overflow: scroll;
    height: 80%;
  }

  table {
    display: block;
    position: relative;
    text-align: center;
  }

  thead {
    position: sticky;
    top: 0;
  }

  thead th {
    height: 80px;
  }

  tbody {
    overflow: scroll;
  }

  tr {
    border: 1px solid #e0e0e0;
    padding-top: 100px;
  }

  th, td {
    border: 1px solid #e0e0e0;
    padding: 30px 20px;
    white-space: nowrap;
  }

</style>

