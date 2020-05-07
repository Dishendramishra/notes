## DBMS

[Keys](#keys)

[Functional Dependencies](#2)



<h4 id="keys">1. Keys</h4>

---

- ##### Types of Keys

A **superkey** of a relation schema $R = {A1, A2, ... , An}$ is a set of attributes $S ⊆ R$ with the property that no two tuples t1 and t2 in any legal relation state r of R will have $t_1[S] = t_2[S]$. 

A **key** K is a superkey with the additional property that removal of any attribute from K will cause K not to be a superkey any more. 

The difference between a key and a superkey is that a **key has to be minimal**

If a relation schema has more than one key, each is called a **candidate key**. 

One of the candidate keys is arbitrarily designated to be the **primary key**, and the others are called **secondary keys**. 



- ##### Prime & Non-Prime Attributes

**prime attribute**: if it is a <u>member</u> of some candidate key. 

**nonprime attribute**:  if it is <u>not a member</u> of any candidate key  



- **Closure Forms**



- ##### Finding all candidates keys

  $Ques.$ Given relation $R(ABCDEFGH)$ 

  and Functional Dependencies
  $$
  AB \rightarrow C  \\
  BD \rightarrow EF  \\
  AD \rightarrow G  \\
  A \rightarrow H
  $$
  $ans.$

  <img src="./fd1.jpg" width=200>

  :warning: First check which attributes are essential attributes (which doesn't have any incoming edges), that will be definitely the part of the key. 

  Hence $A,B,D$ are part of the key.

  $(ABD)^+ = ABCDEFGH \Rightarrow (ABD)^+ = R$

  Hence $ABD$ is a key. 

  If we try to make more keys, that will contain $ABD$, those will be **superkey** but not key (since key must be minimal.)

  

---



<h4 id=2>2. Functional Dependencies</h4>

---

- **Trivial** 												:dart: for $X \rightarrow Y$, iff   $Y \subseteq X$

  FDs like  $A \rightarrow A$ and $AB \rightarrow A$.  

  

- **Non-Trivial**								       :dart: for $X \rightarrow Y$, iff  $Y \cap X = \phi$  

  FDs like $AB \rightarrow C$.  



- **Semi Non-Trivial**							:dart: for $X \rightarrow Y$, iff  $Y \cap X \not= \phi$	and	$Y \not\subseteq X$

  FDs like  $AB \rightarrow AC$.  



- **Inference Rules**

  IR1 (reflexive rule): 			         				If	$X \supseteq Y$ then $X \rightarrow Y$
  IR2 (augmentation rule):  		   					$\{X \rightarrow Y\} \models XZ \rightarrow YZ$
  IR3 (transitive rule):					  					$\{X \rightarrow Y,Y \rightarrow Z \} \models X \rightarrow Z$
  IR4 (decomposition, or projective, rule):  	$\{X \rightarrow YZ\} \models X \rightarrow Y$
  IR5 (union, or additive, rule):. 						$\{X \rightarrow Y,Y \rightarrow Z \} \models X \rightarrow YZ$
  IR6 (pseudo-transitive rule):  	 					$\{X \rightarrow Y,WY \rightarrow Z \} \models WX \rightarrow Z$
  
  
  
  :dart: ​Rules IR1 to IR3 are called **Armstrong’s inference rules.**  

---



#### 3. Normal Forms

---

- #### 1NF

  :dart: All attributes values must be atomic.



- #### 2NF

  :dart: No partial dependency of non-prime attributes is allowed.

  

  **Partial Dependency**: When a non-prime attribute depends on partials attributes of the key.

  e.g. let $R(ABCD)$  and  $AB $ be the key. If a FD like  $B\rightarrow C$ exists, this FD is called partial dependency. Since C partially depends on the key.

  

  ***Definition***: A relation schema R is in second normal form (2NF) if every nonprime attribute A in R is not partially dependent on any key of R.  

  

- #### 3NF

  :dart: No transitive dependencies are allowed.

  

  **Transitive Dependency**: When a non-prime attribute depends on another non-prime attribute.

  e.g. let $R(ABCD)$  and  $AB $ be the key. If a FD like $C \rightarrow D$ exists, this FD is transitive dependency.

  Since $C,D$ are both non-prime attributes.

  

  ***Definition***: relation schema R is in 3NF if it satisfies 2NF and no nonprime attribute of R is transitively dependent on the primary key.  



- #### BCNF  

  :dart: If all FDs,  $\alpha \rightarrow \beta$ ​, $\alpha$ must be a **superkey.** ($\beta$ can be prime or non-prime doesn't matters)

---



1. CRUD
2. ER Diagrams
3. SQL from papers