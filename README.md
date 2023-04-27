# Guinea Pig Partnership and Ancestor App
Daml templates designed to handle guinea pig ownership and guinea pig offspring production. Two guinea pigs can be paired into couples to produce offspring.
Couples can be broken up again by their respective owners, and guinea pigs can be gifted to a different owner if both parties agree to it.
Guinea pigs remember one of their ancestors.

### I. Overview 
This project was created by using the `empty-skeleton` template. The project adopts and exemplifies the `proposal-accept` design pattern. A signatory can create a CoupleRequest contract. Then they can exercise the ProposeCoupleRequest choice as a controller to get the CoupleRequest proposal either approved or rejected by the other owner. If the other owner rejects the requests, than the two guinea pigs are not a couple. Upon exercising the AcceptCoupleRequest choice, a Couple contract is created.

### II. Workflow
1. The owner of a guinea pig may send a request to pair two guinea pigs into a couple.
2. The owner of the other guinea pig (which may be the same owner) can either accept or refuse the request.
3. Once accepted, the couple may produce offspring which is owned by the party that initiated the pairing.
4. At any point, the couple may be broken up by either party.
5. Guinea pigs can produce unexpected offspring, that is offspring with illegitimate partners.

### III. Challenge(s)
* Guinea Pigs need to be publically viewable. We have to add a public party and make every user `canReadAs public`. The respective code is taken from `daml new demo1 --template create-daml-app` and simplified.
* The project was created by using `empty-skeleton` and the following was removed from `daml.yaml`:
```
sandbox-options:
   - --wall-clock-time
```
and replaced with the following:

```
exposed-modules:
  - Main
navigator-options:
 - --feature-user-management=false
```
For more info, check out [this post](https://discuss.daml.com/t/sandbox-options-wall-clock-time/5692/16?u=cathy_jung) on Daml Forum and [Daml Doc](https://docs.daml.com/tools/navigator/index.html?&_ga=2.48248804.337210607.1673989679-241632404.1672853064&_gac=1.17025355.1673455980.CjwKCAiA2fmdBhBpEiwA4CcHzfI2w1_D95zAr3_d6QTypOMXGTpUxtS06c55inucNwZvUZn4AebsJxoCZEgQAvD_BwE&_gl=1*elem6v*_ga*MjQxNjMyNDA0LjE2NzI4NTMwNjQ.*_ga_GVK9ZHZSMR*MTY3Mzk5NDQzOS4zMS4xLjE2NzM5OTQ3MDcuMC4wLjA.#logging-in-as-a-party).


### IV. Building
To compile the project
```
$ daml build
```

### V. Testing
To test all scripts:
Either run the pre-written script in the `Test.daml` under /daml OR run:
```
$ daml start
```

### VI. Running
To load the project into the sandbox and start navigator:
```
$ daml start
```
