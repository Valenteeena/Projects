<template>
    <div class="tableScroller">
      <table class="projTbl">
        <thead>
          <tr>
            <th v-for="c in columns" :key="columns[c]">{{c}}</th>
          </tr>
        </thead>
        <tbody>
        <tr v-for="row in rowData" :key="rowData[row]">
                  <td>{{row.project_name}}</td>
                  <td>{{row.developer}}</td>
                  <td>{{row.main_contractor}}</td>
                  <td>{{row.address}}</td>
                  <td>{{row.state}}</td>
                  <td>{{row.status}}</td>
                  <td>{{row.sector}}</td>
              </tr>
      </tbody>
      </table>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'tableView',
  data(){
    return{
      //Table columns array
      columns: ['Project Name','Developer','Main Contractor','Area','State','Status','Sector'],
      //table row data array
      rowData: []
    }
  },
   mounted() {
        axios
            .get('https://244b8df3-7491-4cfd-a48b-267f19446372.mock.pstmn.io/')
            .then(response => (
              this.rowData = response.data.data
            ))
    }
}
</script>

<style scoped lang='scss'>
  $primary-color: #28394b;
  $table-color: #f6fafd;
  $font-family: Arial, sans-serif;

  .tableScroller{
    color:$primary-color;
    margin: auto;
    overflow-x: scroll;
    overflow-y: visible;
    padding-bottom: 5px;
    margin-top: 3rem;
    margin-left: 189px;
    border-top-right-radius: .5rem;
    box-shadow: 0 2px 3px 0 rgba(219,248,227, 0.5), 0 6px 8px 0 rgba(0, 0, 0, 0.19);

    .projTbl{
      text-align: left;
      border: none;
      border-spacing: 0;
      font: normal 12px $font-family;
      border-radius: .5rem;
      width:100.5%;
      margin: auto;

        th{
        background-color: $primary-color ;
        color:white;
        font-weight: bold;
        height:3.5rem;
        border-style: none;
        padding-left: .5rem;
        width: auto;
        }

        td{
        color: $primary-color;
        padding-left: .5rem;
        padding-right: 10px;
        text-transform: capitalize;        
        width:auto;
        height:3.5rem;
        }
        td:first-child{
          font-weight: bold;
          position: absolute;
          width:185px;
          left: 0;
          top: auto;
          box-sizing: border-box;
          padding-top: 20px;
          height:3.6rem;
        }
        th:first-child{
          position: absolute;
          width:190px;
          left:0;
          border-top-left-radius: .5rem;
          padding-top: 20px;
          box-sizing: border-box;
          height:3.6rem;
        }
        tr:nth-child(odd){
          background-color: $table-color;
        }
        tr:nth-child(odd) > td:nth-child(odd){
          background-color: $table-color;
          box-sizing: border-box;
        }
    }
  }
  @media only screen and(max-width:800px),
    only screen and (max-device-width: 800px){ 
     .tableScroller{
       margin-left: 0 !important;
      .projTbl{
        td:first-child{
          position: unset!important;
          padding-top: 0;
        }
        th:first-child{
          position: unset!important;
          padding-top: 0;
        }
      }
    }
  }
</style>
