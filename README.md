# Idea:
1. Read this dataset - your choice of processing engine

2.  Insert the record to a table per symbol
3. measure overall time to execute the full pipeline
4. Write a basic test
5. document this into a README / github project on how to run your code

#
# WorkFlow

* Read csv in Databricks community acc.
* Replace all special chars with ''
* Get a list of all distinct cryptos
* Go through DataFrame filter for each crypto \
-> add filtered rows to a table with name - crypto_{name}

* Timed the entire process

# Run the following code

import time
start = time.time()

cryptos = read_csv()

final_df = cryptos.withColumn('Symbol', clean_symbol_udf(F.col('Symbol')))

final_df = final_df.filter(F.col('Symbol')!='')

transform_table(final_df, symbols)

stop = time.time()

print('===\nTime: ',stop-start,'\n===')
