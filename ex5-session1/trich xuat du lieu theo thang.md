SELECT 
  user_id,
  EXTRACT(MONTH FROM transaction_date) AS month,
  EXTRACT(YEAR FROM transaction_date) AS year,
  SUM(CASE WHEN type = 'income' THEN amount ELSE 0 END) AS total_income,
  SUM(CASE WHEN type = 'expense' THEN amount ELSE 0 END) AS total_expense
FROM transactions
GROUP BY user_id, year, month;