# WP2.6-Market-Simulator
This tool clears the energy, secondary and tertiary markets, considering cross-border trading through a flow-based market coupling approach.

## Running the tool

To run the tool, the following command must be run:
```
python main.py [boolean] [boolean] [boolean]
```
The three boolean arguments refer to their respective market: **energy**, **secondary** and **tertiary**. Setting the argument to:
- **True**:  will clear the correspoding market.
- **False**: will ignore the corresponding market clearing optimization.

## Input data

To run the Market Simulator there are 4 input folders: network, energy, secondary and tertiary.

The network folder input files are mandatory for every optimization.

On the other hand, the energy, secondary and tertiary folders input files are only required if that market is being cleared. 

**All input files are in csv format**.

### Input folders
#### network
The network folder must have the following files:
- *generators.csv*
- *loads_info.csv*
- *branches.csv*
- *buses.csv*

#### energy
The network folder must have the following files:
- *gen_bid_prices.csv*
- *gen_bid_qnt.csv*
- *load_bid_prices.csv*
- *load_bid_qnt.csv*

#### secondary
The network folder must have the following files:
- *gen_bid_prices.csv*
- *gen_bid_qnt.csv*
- *sec_req.csv*

#### tertiary
The network folder must have the following files:
- *gen_bid_prices.csv*
- *gen_bid_qnt.csv*
- *ter_req.csv*

