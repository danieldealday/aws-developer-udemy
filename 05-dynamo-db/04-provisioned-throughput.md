# Provisioned Throughput

## Read & Write Capacity Units
- provisioned throughput is measured in Capacity Units
- when you create your table, you can specify your requirements in terms of Read Capacity Units and Write Capacity Units
- 1 x Write Capacity Unit = 1 x 1KB Write per second
- 1 x Read Capacity Unit = 1 x 1KB Strongly Consistent Read of 4KB per second OR 2 x Eventually Consistent Read of 4KB per second (Default)

## Example Configuration
- Table with 5 x Read Capacity Units and 5 x Write Capacity Units
- this configuration will be able to perform:
  - 5 x 4KB Strongly Consistent reads = 20KB per second
  - twice as many Eventually Consistent = 40KB
  - 5 x 1KB Writes = 5KB per second
- if your application reads or writes larger items it will consume more Capacity Unites and will cost you more as well

## Strongly Consistent Reads Calculatoin
- your application needs to read 80 items (table rows) per second
- each item 3KB in size
- you need Strongly Consistent Reads
- first, calculate how many Read Capacity Units needed for each read
  - Size of Each Item / 4KB
    - round-up to the nearest whole number, each read will need 1 x Ready Capacity Unit per read operation
    - multiplied by the number of reads per second = 80 Read Capacity Units required

## Eventual Consistent Reads Calculation
- 2 x 4KB reads per second or DOUBLE the through put of Strongly Consistent reads
- Size of Each Item / 4KB
  - round-up to the nearest whole number
  - multiply the number of reads per second = 80
  - divide 80 by 2, so you only need 40 Read Capacity Units for Eventually Consistent reads

## Wrie Capacity Units Calculation
- you want to write 100 items per second
- each item is 512bytes in size
- first calculate how many Capacity Units for each write
  - Size of Each Item / 1KB (for Write Capacity Units)
- round-up to the nearest whole number, each write will need 1 x Write Capacity Unit per write operation
- multiplied by the number of writes per second = 100 Write Capacity Units required

## Tips
- provisioned throughput is measured in capacity units
- 1 x write capacity unit = 1 x 1KB write per second
- 1 x read capacity unit = 1 x 4KB strongly consistent read OR 2 x 4KB eventually consistent reads per second