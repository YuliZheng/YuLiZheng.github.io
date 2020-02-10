## VC Dimension

In a learning model, if f is needed to to approximated, and we use training data D to choose a function in set H.
$$
E_{train}(h)=\frac{1}{n}\sum h(x)\not=y
\\E_{r}(h)=E[h(x)\not=f(x)]
$$
We can only know E_train but we cannot get E_r.

- $$
  P(|x-E[x]|>\epsilon)\le2exp(-2\epsilon^2n)
  $$

  This is an inequality we know.

  So if h is fixed and training data is picked
  $$
  P(|E_{train}(h)-E_r(h)|>\epsilon)\le2exp(-2\epsilon^2n)
  $$
  Now
  $$
  P(\exist h\in H\ s.t.\ |E_{train}-E_{r}|>\epsilon)\le 2 M\cdot exp(-2\epsilon^2n)\\
  M=|H|
  $$
  But M is infinite sometime and we want to use another constant much smaller than it to get a better bound.

  - How to get a number?

    Define:

    For any given set of x, define
    $$
    m_H(n,x)=|H(x)|
    $$
    Then
    $$
    m_H(n)=\max_{x}m_H(n)
    $$
    mH(n) stands for the maximum kind of result H can give in the input of X.

    Note
    $$
    m_H(n)\le2^n
    $$
    Define
    $$
    k=\min\{k|m_H(k)<2^k\}
    $$
    If k is not infinity

    - If k exists
      $$
      m_H(n)=O(n^{k-1})
      $$
      **proof**

      ​	After considering the point relation, we could have
      $$
      m_H(N)|k=m_H(N-1)|k+m_H(N-1)|k-1
      $$
      ​	We omit the proof of this formula here.

      ​	Using this formula we can deduce this lemma.

    Now we have a number mH(N) and we know it is bound by poly of N when there is some value.

    We next want to prove that this can be used.
    $$
    P(\exist h\in H\ s.t.\ |E_{train}-E_{r}|>\epsilon)\le 2 m_H(n) exp(-2\epsilon^2n)
    $$
    Indeed, now we only do that

  - $$
    P(\exist h\in H\ s.t.\ |E_{train}-E_{r}|>\epsilon)\le 8 m_H(2n) exp(-\frac{\epsilon^2}{8}n)
    $$

    Proof:

    - Let D1 be another data randomly picked from X and having the same number of D.

      Claim:
      $$
      P(\exist h\in H\ s.t.\ |E_{train}-E_r|>\epsilon)\le2P(\exist h\in H\ s.t.\ |E_{train}-E_{D1}|>\frac{\epsilon}{2})
      $$
      Proof:
      $$
      I_{|E_{train}-E_r|>\epsilon}I_{|E_r-E_{D1|}<\frac{\epsilon}{2}}\le I_{|E_{train}-E_{D1}|>\frac{\epsilon}{2}}
      $$
      Taking expectation over D1
      $$
      I_{|E_{train}-E_r|>\epsilon}P(|E_r-E_{D1}|<\frac{\epsilon}{2})\le P(|E_{train}-E_{D1}|>\frac{\epsilon}{2})
      $$
      It's known
      $$
      P(|E_r-E_{D1}|\ge\frac{\epsilon}{2})\le\frac{4varh(x)}{N\epsilon^2}\\
      varh(x)\le\frac{1}{4}
      $$
      If
      $$
      n\epsilon^2\ge\frac{1}{2}
      $$
      Then
      $$
      P(|E_r-E_{D1}|<\frac{\epsilon}{2})\le\frac{1}{2}
      $$

      $$
      I_{|E_{train}-E_r|>\epsilon}\le2P(|E_{train}-E_{D1}|>\frac{\epsilon}{2})
      $$

      $$
      P(|E_{train}-E_r|>\epsilon)\le2P(|E_{train}-E_{D1}|>\frac{\epsilon}{2})
      $$

    - For any given h

      Claim:
      $$
      P(\exist h\in H\ s.t.\ |E_{train}-E_{D1}|>\frac{\epsilon}{2})\le m_H(2n)P(|E_{train}(h)-E_{D1}(h)|>\frac{\epsilon}{2})
      $$
      Proof:
      $$
      P(\exist h\in H\ s.t.\ |E_{train}-E_{D1}|>\frac{\epsilon}{2})\le \sum_{h\in H}P(|E_{train}(h)-E_{D1}(h)|>\frac{\epsilon}{2})
      $$
      There is only mH(2N) h in H that E(h)-ED1(h) is not the same. so
      $$
      P(\exist h\in H\ s.t.\ |E_{train}-E_{D1}|>\frac{\epsilon}{2})\le m_H(2n)P(|E_{train}(h)-E_{D1}(h)|>\frac{\epsilon}{2})
      $$

    - $$
      P(\exist h\in H\ s.t.\ |E_{train}-E_r|>\epsilon)\le2P(\exist h\in H\ s.t.\ |E_{train}-E_{D1}|>\frac{\epsilon}{2})\\
      \le 2m_H(2n)P(|E_{train}(h)-E_{D1}(h)|>\frac{\epsilon}{2})
      $$

      $$
      P(|E_{train}(h)-E_{D1}(h)|>\frac{\epsilon}{2})\le P(|E_{r}(h)-E_{train}(h)|>\frac{\epsilon}{4}\or|E_{r}(h)-E_{train}(h)|>\frac\epsilon4)\\
      \le4exp(-\frac{\epsilon^2}{8}n)\\
      P(\exist h\in H\ s.t.\ |E_{train}-E_r|>\epsilon)\le8m_H(2n)exp(-\frac{\epsilon^2}8n)
      $$

Now if H have a k (good H) and n is large (good n)
$$
P(\exist h\in H\ s.t.\ |E_{train}-E_r|>\epsilon\le8m_H(2n)exp(-\frac{\epsilon^2}8n)\\
\le8O(n^{k-1})exp(-\frac{\epsilon^2}8n)\to0
$$
So we know that the training result tends to approximate.

Now define the VC dimention of H to be k-1.

<img src="C:\Users\VIAN33\AppData\Roaming\Typora\typora-user-images\image-20200208210342966.png" alt="image-20200208210342966" style="zoom:50%;" />

With small vc dimention, it is easy to make the train result similar to test result, but not simple to decrease train result, with large vc dimention, it is not easy to make the train result similar to test result, but simple to decrease train result.











