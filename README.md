Download Link: https://assignmentchef.com/product/solved-stat542-assignment-2
<br>
Implement the EM algorithm for a <em>p</em>-dimensional Gaussian mixture model with <em>G </em>components:

<em>G</em>

X

<em>p<sub>k </sub></em>· <strong>N</strong>(<em>x</em>;<em>µ<sub>k</sub>,</em>Σ)<em>. </em><em>k</em>=1

Store the parameters as a list in R with three components

<ul>

 <li>prob: a <em>G</em>-dimensional probability vector;</li>

 <li>mean: a <em>p</em>-by-<em>G </em>matrix with the <em>k</em>-th column being <em>µ<sub>k</sub></em>, the <em>p</em>-dimensional mean for the <em>k</em>-th Gaussian component;</li>

 <li>Sigma: a <em>p</em>-by-<em>p </em>covariance matrix shared by all <em>G </em></li>

</ul>

Your code should have the following structure.

<table width="528">

 <tbody>

  <tr>

   <td width="528">Estep &lt;- function(data, G, para){# Your Code# return the n-by-G probability matrix}Mstep &lt;- function(data, G, para, post.prob){# Your Code# Return the updated parameters}myEM &lt;- function(data, T, G, para){ for(t in 1:T){ post.prob &lt;- Estep(data, G, para) para &lt;- Mstep(data, G, para, post.prob)} return(para)}</td>

  </tr>

 </tbody>

</table>

You should test your code on the faithful data from the R package mclust with <em>G </em>= 2. The estimated parameters from your algorithm and the one from mclust after <em>T </em>= 10 iterations should be the same.

<table width="528">

 <tbody>

  <tr>

   <td width="528">library(mclust)n &lt;- nrow(faithful) Z &lt;- matrix(0, n, 2)Z[sample(1:n, 120), 1] &lt;- 1 Z[, 2] &lt;- 1 – Z[, 1]ini0 &lt;- mstep(modelName=”EEE”, faithful, Z)$parameters# Output from my EM algpara0 &lt;- list(prob = ini0$pro, mean = ini0$mean,Sigma = ini0$variance$Sigma)myEM(T=10, para=para0)# Output from mclustRout &lt;- em(modelName = “EEE”, data = faithful, control = emControl(eps=0, tol=0, itmax = 10), parameters = ini0)$parameterslist(Rout$pro, Rout$mean, Rout$variance$Sigma)</td>

  </tr>

 </tbody>

</table>