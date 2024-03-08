# Query-Languages

# Query Question
### Find the second highest amount

```sql
select * from payment;

select amount from payment
group by amount
order by amount DESC
limit 1 offset 1;

select max(amount) from payment
where amount not in (select max(amount) from payment);
```