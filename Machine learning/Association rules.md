
Association rules are elements that appear "frequently" in objects. For example, in a dataset of shopping carts where each row is a cart and each dimension an element in the cart, we could try to find association rules between items frequently bought together like Nutella and bread or salt and pepper.

## Some definitions

- __Itemset__: a collection of one or more items. Example: {Nutella, Milk}
- __K-itemset__: an itemset containing k items.
- __Support count$(\sigma)$__: frequency of occurence of an itemset in a dataset.
- __Support__: fraction of rows containing a given itemset. Example: 3/5 with 3 rows containing the given itemset and 5 total rows.
- __Frequent Itemset__: an itemset whose support is grater or equal to a given trashold
- __Association Rule__: A -> C with A, C itemset and A antecedent, C consequent
- __Rule evaluation metrics__:
	- __Support (sup)__: Fraction of the dataset containing both A and C
	- __Confidence (conf)__: Measures how often C appears when A does.
$$
\begin{align}
sup = \frac{\sigma(A, C)}{N}\\
conf = \frac{\sigma(A, C)}{\sigma(A)}
\end{align}
$$

## Association rule mining task

We want to find a set of association rules that has sup and conf > then a given trashold. In order to do so we can use different approaches:
- Bruteforce: try all and prune the bad ones (wery expensive, impossible to compute)
- Frequently item generation: generate all items with support grater than the trashold and, from them, generate rules. Still very computationally expensive
- Apriori principle: Given an itemset i, if that itemset is infrequent then, all the itemset j containing i ($i \in j$) are infrequent => cut them. On the opposite, foreach item i frequent, all of his components j ($j \in i$) must be frequent => consider them


## Association rule frequent itemset generation

Let's assume to have a table with only the frequent itemset of size k. We want to generate the itemsets of size k+1. We can do it in three steps:
Step 1: generate all the possible candidates (here in sql)
```sql 
insert into Ck1
select p.item1, p.item2, ..., p.itemk, q.item1, ... q.itemk
from Lk p, Lk q
where p.item1 = p.item2 and ... and p.itemk < q.itemk;
```

Step 2: prune the candidates' table ck1:
```python
def prune():
	items = getCKitems()
	for c in items:
		for s in subsets(c, k - 1):
			if not s in FrequentItems(k - 1)
				removeFromCk(c)
```

Step 3: generate the new frequent itemset of size k + 1
```python
def generate():
	k = 1
	Lk = get_frequent_itemset(k)
	while len(Lk) > 0:
		Ck = generate_items_in_step_one(Lk)
		update_support_count(Ck)
		Lk = [c if sup(c) > minsup for c in Ck]
		k += 1
	return k, Lk
```



## Rule generation

```python
def rule_generator(L): #L is a list of frequent itemset
	rules = []
	for l in subsets(L):
		f = association_rule(l, L - l) # l => L - l 
		if conf(f) >= confidence_trashold:
			rules.append(f)
	return rules
```

## Interestingness

The generation process tends to build a lot of association rules with a lot of them that are not usefull or interesting. We could build a contincecy table to measure the interestingness of a rule:
|           | $C$      | $\bar{C}$ |          |
| --------- | -------- | --------- | -------- |
| $A$       | $f_{11}$ | $f_{10}$  | $f_{1+}$ |
| $\bar{A}$ | $f_{01}$ | $f_{00}$  | $f_{0+}$ |
|           | $f_{+1}$ | $f_{+0}$          |          |

There can be sitation where $A \Rightarrow C$ has a high confidence (computed as $\frac{f_{11}}{f_{1+}}$) but the probability $P(C|\bar{A})$ (computed as $\frac{f_{01}}{f_{0+}}$) higher than the confidence of the rule and that invalidates the rule itself.



## Statistical based measures

### Lift

$$
\text{lift}(A \Rightarrow C) = \frac{conf(A \Rightarrow C)}{sup(C)} = \frac{Pr(A,C)}{Pr(A)Pr(C)}
$$
Insenitive to rule direction. It is the ratio of true cases over indipendence

### Leve

$$
leve(A \Rightarrow C) = Pr(A,C) - Pr(A)Pr(C) = sup(A \cup C) - sup(A)sup(C)
$$
Insenitive to rule direction. It is the number of additiona cases over indipendence


### Conviction

$$
conv(A \Rightarrow C) = \frac{1 - sup(c)}{1 - conf(A \Rightarrow C)} = \frac{Pr(A)(1 - Pr(C))}{Pr(A) - Pr(A,C)}
$$

Sensitive to rule direction. It is the ration of expected frequency that A occours without C. Also called novelty


### Intuation about measures

Higher support => rule applies to more record.
Higher confidence => chance that the rule is true for some record is higher.
Higher lift => chanche that the rule is just concidence is lower.
Higher conviction => the rule is violeted less often than it would be if the antecendet and the consequent were indipendent.