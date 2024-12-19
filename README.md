# Data-Analytics-Portfolio
use transactionbank;
show tables;
SELECT 
    *
FROM
    bank_transactions_data_21;
-- Transaction Metrics
SELECT 
    COUNT(transactionID) AS Total_Transctions
FROM
    bank_Transactions_data_21;
SELECT 
    SUM(transactionamount) AS Total_Transaction_Amount
FROM
    bank_transactions_data_21;
SELECT 
    AVG(transactionamount) AS Average_Transaction_Amount
FROM
    bank_transactions_data_21;
-- customer metrics
SELECT 
    COUNT(DISTINCT accountID) AS Active_Customers
FROM
    bank_Transactions_data_21;
SELECT 
    COUNT(Transactionid) / COUNT(DISTINCT accountID) AS AVG_number_of_transaction_per_customer
FROM
    bank_transactions_data_21;
    SELECT 
    SUM(transactionAmount) / COUNT(DISTINCT accountID) AS AVG_transaction_amount_per_customer
FROM
    bank_transactions_data_21;
SELECT 
    *
FROM
    bank_transactions_data_21;
-- channel and merchant metrics
SELECT 
    *
FROM
    bank_transactions_data_21;
SELECT 
    channel,
    COUNT(transactionid) AS transactions,
    SUM(transactionamount) AS total_amount
FROM
    bank_transactions_data_21
GROUP BY channel;
SELECT 
    AVG(accountbalance) AS avg_account_balance
FROM
    bank_transactions_data_21;
-- trend
SELECT 
    DATE(transactiondate) AS transaction_date,
    COUNT(transactionid) AS transactions,
    SUM(transactionamount) AS total_amount
FROM
    bank_transactions_data_21
GROUP BY DATE(transactiondate)
ORDER BY transaction_date;
-- fraud
select accountid,transactionamount,LAG(transactionamount) OVER (PARTITION BY accountid order by transactiondate)as previous_trans_amount from bank_transactions_data_21;

