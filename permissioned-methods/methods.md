# Methods

## **Set Fee Collector**

This method is callable by the fee\_manager. It updates the global state value of fee\_collector to a new address.

## **Set Fee Setter**

This method is callable by the fee\_manager. It updates the global state value of fee\_setter to a new address.

## **Set Fee**

This method is callable by the fee\_setter. It updates the pool local state values of total\_fee\_share and protocol\_fee\_ratio to new values. The protocol enforces limits on the allowable values for each of these. This allows the swap fees of each pool to vary over time without moving or fragmenting liquidity. It is intended that these changes will be made based on sound market analysis for the benefit of the poolers and protocol.

## **Set Fee Manager**

This method is callable by the fee\_manager. It updates the global state value of fee\_manager to a new address.
