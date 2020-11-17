<template>
  <div class="container">
        <table id="detail" class="rtable">
        <thead>
          <tr>
            <th>Project Name</th>
            <th>Developer</th>
            <th>Main Contractor</th>
            <th>Area</th> 
            <th>state</th>
            <th>Status</th>
            <th>Sector</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="detail in details" :key="detail.id">
           <td>{{ detail.project_name }}</td>
          <td>{{ detail.developer }}</td>
          <td>{{ detail.main_contractor }}</td>
          <td>{{ detail.lga }}</td>
          <td>{{ detail.state }}</td>
          <td> <span class="status">{{ detail.status }}</span></td>
          <td>{{ detail.sector }}</td>
          </tr>
        </tbody>
      </table>
  </div>
</template>

<script>
import axios from 'axios';

const url = "https://70c5b72c-65db-4a66-ba01-3e14763157e8.mock.pstmn.io/"
export default {
  name: "DataTable",
  props: {
    msg: String
  },
  data() {
    return {
      error: null,
      details: []
    }
  },
  async mounted() {
    try {
    this.details = await axios.get(url).then(res => res.data.data);
    console.log("Details:", this.details);
    this.error = "Error!!! API not hitted";
  } catch (error) {
    this.details = null;
    this.error = error;
  }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container {
  margin: 2rem;
}
.rtable {
    display: inline-block;
    width: 100%;
    position: relative;
    overflow-x: auto;
    border-collapse: collapse;
    border-spacing: 0;
    cursor: pointer;

    th {
   background-color: rgb(40,57,75);
   font-size: 14px;
   color: white;
   &:first-child {
     border-top-left-radius: 8px;
   }
   &:last-child {
     border-top-right-radius: 8px;
   }
  }

  td {
    font-size: 14px;
  }

  tr:nth-child(even){background-color: #F6FAFD;}

  tr:hover {background-color: #d6e4f0;}

  th:first-child {
  position: -webkit-sticky;
  position: sticky;
  left: 0;
  z-index: 10;
}

  
}

table {
      -webkit-box-shadow: 0px 0px 26px 3px rgba(18, 24, 29, 0.205);
      -moz-box-shadow: 0px 0px 26px 3px rgba(18, 24, 29, 0.205);
      box-shadow: 0px 0px 26px 3px rgba(18, 24, 29, 0.205);
  }
  


.rtable th,
.rtable td {
  padding: 16px 32px;
  text-align: left;
}

.status {
  background: #FDE2B4;
  padding: 0.3rem;
  border-radius: 2px;
}

@media 
only screen and (max-width: 760px),
(min-device-width: 768px) and (max-device-width: 1024px)  {

	/* Force table to not be like tables anymore */
	table, thead, tbody, th, td, tr { 
		display: block; 
	}

 }


// .container  {
//   
//   width: 100%;
// }
// .table-scroll {
// 	position: relative;
//   max-width:100%;
//   width: 1000px;
//   z-index: 10;
//   margin: auto;
//   overflow: auto;
//   height: 600px;
// }

// .table-scroll table {
//   width: 100%;
//   min-width: 1280px;
//   margin: auto;
//   border-collapse: separate;
//   border-spacing: 0;
// }
// .table-wrap {
//   position: relative;
// }
// .table-scroll th,
// .table-scroll td {
//   text-align: left;
//   padding: 2rem 1rem 2rem 1rem;
//   vertical-align: top;
// }

// .table-scroll thead th {
//   padding: 1.5rem 1rem 1.5rem 1rem;
//   text-align: left;
//   background-color: rgb(40,57,75);
//   color: white;
//   position: -webkit-sticky;
//   position: sticky;
//   top: 0;
// }



//  #detail > th:first-child{
//    border-top-left-radius: 1rem;
//  }
// #detail > th:last-child{
//   border-top-right-radius: 0.625rem;
// }

// thead th:first-child,
// tfoot th:first-child {
//   z-index: 5;
// }

// tr:first-child{
//   border-top-left-radius: 0.625rem;
//    border-top-right-radius: 0.625rem;
//  }

// tr:nth-child(even){background-color: #F6FAFD;}

// tr:hover {background-color: #d6e4f0;}

//  #detail  {
//   font-family: Arial, Helvetica, sans-serif;
//   border-collapse: collapse;
//   width: 100%;
//   -webkit-box-shadow: 0px 0px 26px 3px rgba(18, 24, 29, 0.205);
//   -moz-box-shadow: 0px 0px 26px 3px rgba(18, 24, 29, 0.205);
//   box-shadow: 0px 0px 26px 3px rgba(18, 24, 29, 0.205);
  

//  td {
//    text-align: left;
//    padding: 2rem 1rem 2rem 1rem;
//  }

//  th:first-child{
//    border-top-left-radius: 1rem;
//  }
// th:last-child{
//   border-top-right-radius: 0.625rem;
// }
// tr:first-child{
//   border-top-left-radius: 0.625rem;
//    border-top-right-radius: 0.625rem;
// }

//  tr:nth-child(even){background-color: #F6FAFD;}

//  tr:hover {background-color: #d6e4f0;}


// }
</style>
