# arvol

- proof engine using webized prolog which basically means that atoms can be IRIs
- besides top-down reasoning with `conclusion :- premise` rules, it also does bottom-up reasoning with `conclusion :+ premise` rules
- variables are interpreted universally except for `conclusion :+ premise` conclusion-only variables which are interpreted existentially
- bottom-up reasoning can use `stable(n)` to fail if the deductive closure at level `n` is not yet stable
- bottom-up reasoning steps are performed as `step(premise_inst, conclusion_inst)`
- queries are posed as `true :+ premise` and answered as `answer(premise_inst)`
- inference fuses are defined as `false :+ premise` and blown as `fuse(premise_inst)` with return code 2

## rationale for bottom-up reasoning

- conclusion can be a conjunction
- conclusion can be `false` to blow an inference fuse
- conclusion can be `true` to pose a query
- conclusion can not be any other built-in
- conclusion-only variables are existentials
- performing bottom-up steps `step/2`
- avoiding loops that could occur with top-down reasoning

## installation and test

- install [trealla](https://github.com/trealla-prolog/trealla#building)
- run the tests
    ```
    git clone https://github.com/eyereasoner/arvol
    cd arvol/etc
    ./test
    ```

## background

- personal notes by Tim Berners-Lee: [Design Issues](https://www.w3.org/DesignIssues/)
- book of Markus Triska: [The Power of Prolog](https://www.metalevel.at/prolog)
