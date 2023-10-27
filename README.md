# WP2.6-Market-Simulator
This tool clears the energy, secondary and tertiary markets, considering cross-border trading through a flow-based market coupling approach.

---

## Running the tool

To run the tool, the following command must be run:
```
python main.py [boolean] [boolean] [boolean]
```
The three boolean arguments refer to their respective market: **energy**, **secondary** and **tertiary**. 

Setting the argument to:
- **True**:  will clear the correspoding market.
- **False**: will ignore the corresponding market clearing optimization.

---

## Input data

To run the Market Simulator there are 4 input folders: network, energy, secondary and tertiary.

The network folder input files are mandatory for every optimization.

On the other hand, the energy, secondary and tertiary folders input files are only required if that market is being cleared. 

**All input files are in csv format**.

### network folder

*generators.csv*
  <table class="table table-bordered">
    <thead class="thead-light">
      <tr><th>Element</th><th>Description</th></tr>
    </thead>
    <tbody>
      <tr><td><a>gen_id</a></td><td>identification code of a generator</td></tr>
      <tr><td><a>bus</a></td><td>bus number where the generator is connected</td></tr>
      <tr><td><a>fixed_cost</a></td><td>fixed generator costs value in €/pu</td></tr>
      <tr><td><a>variable_cost</a></td><td>variable generator costs value in €/pu</td></tr>
      <tr><td><a>r_up</a></td><td>amount of energy that the generator is able to increase in production between periods</td></tr>
      <tr><td><a>r_down</a></td><td>amount of energy that the generator is able to decrease in production between periods</td></tr>
      <tr><td><a>LGC</a></td><td>boolean value to indicate if the energy market optimization considers the generator load gradient curve for complex orders</td></tr>
      <tr><td><a>MIC</a></td><td>boolean values to indicate if the energy market optimization considers the generator minimum income coefficient for the complex order</td></tr>
    </tbody>
  </table>

*loads_info.csv*
  <table class="table table-bordered">
    <thead class="thead-light">
      <tr><th>Element</th><th>Description</th></tr>
    </thead>
    <tbody>
      <tr><td><a>load_id</a></td><td>identification code of a load</td></tr>
      <tr><td><a>bus</a></td><td>bus number where the generator is connected</td></tr>
    </tbody>
  </table>

*branches.csv*
  <table class="table table-bordered">
    <thead class="thead-light">
      <tr><th>Element</th><th>Description</th></tr>
    </thead>
    <tbody>
      <tr><td><a>branch_id</a></td><td>identification code of a branch</td></tr>
      <tr><td><a>bus0</a></td><td>bus where the branch starts</td></tr>
      <tr><td><a>bus1</a></td><td>bus where the branch ends</td></tr>
      <tr><td><a>r</a></td><td>resistance value in p.u.</td></tr>
      <tr><td><a>x</a></td><td>reactance value in p.u.</td></tr>
      <tr><td><a>b</a></td><td>susceptance value in p.u.</td></tr>
      <tr><td><a>s_nom</a></td><td>nominal power of the line in p.u.</td></tr>
    </tbody>
  </table>
    
*buses.csv*	
  <table class="table table-bordered">
    <thead class="thead-light">
      <tr><th>Element</th><th>Description</th></tr>
    </thead>
    <tbody>
      <tr><td><a>bus_id</a></td><td>identification code of a bus</td></tr>
      <tr><td><a>zone</a></td><td>zone number from where the bus is from</td></tr>
      <tr><td><a>slack</a></td><td>fboolean value to represent the slack bus</td></tr>
    </tbody>
  </table>

#### energy folder

*gen_bid_prices.csv*
  
  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>Element</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>gen_id</a></td><td>identification code of a generator</td></tr>
    <tr><td><a>n columns</a></td><td>n amount of columns that represent each timestep to run with each value representing the respective generator bid</td></tr>
  </tbody>
</table>

*gen_bid_qnt.csv*

  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>Element</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>gen_id</a></td><td>identification code of a generator</td></tr>
    <tr><td><a>n columns</a></td><td>n amount of columns that represent each timestep to run with each value representing the respective generator bid</td></tr>
  </tbody>
</table>

*load_bid_prices.csv*

  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>Element</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>load_id</a></td><td>identification code of a load</td></tr>
    <tr><td><a>n columns</a></td><td>n amount of columns that represent each timestep to run with each value representing the respective load bid</td></tr>
  </tbody>
</table>

*load_bid_qnt.csv*

  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>Element</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>load_id</a></td><td>identification code of a load</td></tr>
    <tr><td><a>n columns</a></td><td>n amount of columns that represent each timestep to run with each value representing the respective load bid</td></tr>
  </tbody>
</table>

#### secondary folder

*gen_bid_prices.csv*

  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>Element</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>gen_id</a></td><td>identification code of a generator</td></tr>
    <tr><td><a>n columns</a></td><td>n amount of columns that represent each timestep to run with each value representing the respective generator bid</td></tr>
  </tbody>
</table>

*gen_bid_qnt.csv*

  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>Element</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>gen_id</a></td><td>identification code of a generator</td></tr>
    <tr><td><a>n columns</a></td><td>n amount of columns that represent each timestep to run with each value representing the respective generator bid</td></tr>
  </tbody>
</table>

*sec_req.csv*

  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>Element</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>gen_id</a></td><td>identification code of a zone</td></tr>
    <tr><td><a>n columns</a></td><td>n amount of columns that represent each timestep to run with each value representing the respective zone secondary reserve requirements</td></tr>
  </tbody>
</table>

#### tertiary folder

*gen_bid_prices.csv*

  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>Element</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>gen_id</a></td><td>identification code of a generator</td></tr>
    <tr><td><a>n columns</a></td><td>n amount of columns that represent each timestep to run with each value representing the respective generator bid</td></tr>
  </tbody>
  </table>

*gen_bid_qnt.csv*

  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>Element</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>gen_id</a></td><td>identification code of a generator</td></tr>
    <tr><td><a>n columns</a></td><td>n amount of columns that represent each timestep to run with each value representing the respective generator bid</td></tr>
  </tbody>
</table>

*ter_req.csv*
  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>Element</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>gen_id</a></td><td>identification code of a zone</td></tr>
    <tr><td><a>n columns</a></td><td>n amount of columns that represent each timestep to run with each value representing the respective zone tertiary reserve requirements</td></tr>
  </tbody>
</table>

---

## Output data

To Market Simulator generates all outputs in **csv format**. The market results are inserted into their respective folder. Each folder content is as follows:

### energy folder
  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>File</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>results_gen</a></td><td>generators energy market clearance results for the timesteps defined in the input folders</td></tr>
    <tr><td><a>results_load</a></td><td>loads energy market clearance results for the timesteps defined in the input folders</td></tr>
  </tbody>
</table>

### secondary folder

  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>File</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>results_secondary</a></td><td>generators secondary market clearance results for the timesteps defined in the input folders</td></tr>
  </tbody>
</table>

### tertiary folder

  <table class="table table-bordered">
  <thead class="thead-light">
    <tr><th>File</th><th>Description</th></tr>
  </thead>
  <tbody>
    <tr><td><a>results_tertiary</a></td><td>generators tertiary market clearance results for the timesteps defined in the input folders</td></tr>
  </tbody>
</table>


