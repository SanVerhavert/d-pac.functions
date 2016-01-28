# d-pac.functions

## Installation

```sh
$ npm install d-pac.functions
```

## Usage

```js
const funx = require('d-pac.functions');

funx.stat.square(10); //100
funx.pm.reliability(2.6246692913372702, 0.7615773105863908);// 0.9158064516129032
```

```js
const stat = require('d-pac.functions/stat');
stat.square(10); //100
```

```js
const pm = require('d-pac.functions/pm');
pm.reliability(2.6246692913372702, 0.7615773105863908);// 0.9158064516129032
```

## API

<a name="stat"></a>
## stat : <code>object</code>
**Kind**: global namespace  

* [stat](#stat) : <code>object</code>
    * [.square(value)](#stat.square) ⇒ <code>Number</code>
    * [.sum(list, [f])](#stat.sum) ⇒ <code>Number</code>
    * [.mean(list, [f])](#stat.mean) ⇒ <code>Number</code>
    * [.variance(list, [f])](#stat.variance) ⇒ <code>Number</code>
    * [.sd(list, [f])](#stat.sd) ⇒ <code>Number</code>
    * [.rms(list, [f])](#stat.rms) ⇒ <code>Number</code>

<a name="stat.square"></a>
### stat.square(value) ⇒ <code>Number</code>
Squares a number

**Kind**: static method of <code>[stat](#stat)</code>  

| Param | Type |
| --- | --- |
| value | <code>Number</code> | 

**Example**  
```js
stat.square(10); //100
```
<a name="stat.sum"></a>
### stat.sum(list, [f]) ⇒ <code>Number</code>
Addition of a sequence of numbers - ∑

**Kind**: static method of <code>[stat](#stat)</code>  

| Param | Type |
| --- | --- |
| list | <code>Array</code> | 
| [f] | <code>function</code> | 

**Example**  
```js
stat.sum([1, 2, 3, 5, 8 ]); //19
```
**Example**  
```js
stat.sum([{v:1}, {v:2}, {v:3}, {v:5}, {v:8}], (item)=> item.v); //19
```
<a name="stat.mean"></a>
### stat.mean(list, [f]) ⇒ <code>Number</code>
Arithmetic mean, sum of a sequence of numbers divided by sequence length

**Kind**: static method of <code>[stat](#stat)</code>  

| Param | Type |
| --- | --- |
| list | <code>Array</code> | 
| [f] | <code>function</code> | 

**Example**  
```js
stat.mean([1, 2, 3, 5, 8 ]); //3.8
```
**Example**  
```js
stat.mean([{v:1}, {v:2}, {v:3}, {v:5}, {v:8}], (item)=> item.v); //3.8
```
<a name="stat.variance"></a>
### stat.variance(list, [f]) ⇒ <code>Number</code>
The distance between numbers in a set

**Kind**: static method of <code>[stat](#stat)</code>  

| Param | Type |
| --- | --- |
| list | <code>Array</code> | 
| [f] | <code>function</code> | 

**Example**  
```js
stat.variance([1, 2, 3, 5, 8 ]); //6.16
```
**Example**  
```js
stat.variance([{v:1}, {v:2}, {v:3}, {v:5}, {v:8}], (item)=> item.v); //6.16
```
<a name="stat.sd"></a>
### stat.sd(list, [f]) ⇒ <code>Number</code>
Standard deviation - σ

**Kind**: static method of <code>[stat](#stat)</code>  

| Param | Type |
| --- | --- |
| list | <code>Array</code> | 
| [f] | <code>function</code> | 

**Example**  
```js
stat.sd([1, 2, 3, 5, 8 ]); //2.4819347291981715
```
**Example**  
```js
stat.sd([{v:1}, {v:2}, {v:3}, {v:5}, {v:8}], (item)=> item.v); //2.4819347291981715
```
<a name="stat.rms"></a>
### stat.rms(list, [f]) ⇒ <code>Number</code>
Root mean square, quadratic mean

**Kind**: static method of <code>[stat](#stat)</code>  

| Param | Type |
| --- | --- |
| list | <code>Array</code> | 
| [f] | <code>function</code> | 

**Example**  
```js
stat.rms([1, 2, 3, 5, 8 ]); //4.538722287164087
```
**Example**  
```js
stat.rms([{v:1}, {v:2}, {v:3}, {v:5}, {v:8}], (item)=> item.v); //4.538722287164087
```

<a name="pm"></a>
## pm : <code>object</code>
**Kind**: global namespace  

* [pm](#pm) : <code>object</code>
    * [.reliability(sd, rmse)](#pm.reliability) ⇒ <code>number</code>
    * [.reliabilityFunctor(getAbility, getSE)](#pm.reliabilityFunctor) ⇒ <code>function</code>

<a name="pm.reliability"></a>
### pm.reliability(sd, rmse) ⇒ <code>number</code>
Overall consistency of a measure

**Kind**: static method of <code>[pm](#pm)</code>  

| Param | Type | Description |
| --- | --- | --- |
| sd | <code>number</code> | Standard deviation |
| rmse | <code>number</code> | RMS of the SE |

**Example**  
```js
pm.reliability(4, 2); //0.75
```
<a name="pm.reliabilityFunctor"></a>
### pm.reliabilityFunctor(getAbility, getSE) ⇒ <code>function</code>
Creates a function by taking two getters, which can be used to calculate the reliability of a set of values and SE's

**Kind**: static method of <code>[pm](#pm)</code>  

| Param | Type | Description |
| --- | --- | --- |
| getAbility | <code>function</code> | getter for ability |
| getSE | <code>function</code> | getter for standard error |

**Example**  
```js
const list = [{v:1, se:4}, {v:2, se:2}, {v:3, se:0}, {v:5, se:0.45}, {v:8, se:3}];
const f = pm.reliabilityFunctor((item)=>item.v, (item)=>item.se);
f(list); //0.05186688311688284
```
