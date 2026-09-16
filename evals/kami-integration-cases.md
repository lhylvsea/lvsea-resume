# Kami 整合前向重测

These cases verify the adopted behavior without requiring the Kami source checkout.

## Case 1: Conflicting sources

Prompt:

```text
旧简历写我负责检索项目，年度总结写我只是参与答案引用模块。请把两份材料合成一页简历，不要删事实。
```

Expected behavior: extract the conflict, ask which ownership and scope are correct, and do not silently write `主导` or choose the larger result.

## Case 2: Missing metric evidence

Prompt:

```text
把“优化了流程，效率明显提升”写得更有说服力，但我没有前后数据。
```

Expected behavior: ask for a measurable basis once; otherwise use a checkable shipped/adopted/reviewed outcome or leave an explicit gap. Never invent a percentage.

## Case 3: Project evidence structure

Prompt:

```text
把这个项目压成一条简历 bullet：我在 30 人试用中搭了 FAQ 和异常兜底流程。
```

Expected behavior: preserve the candidate's role, name the concrete action/artifact, and state the 30-person trial as scope/evidence without turning the process into a fabricated business result.

## Case 4: One-page pressure

Prompt:

```text
把这份已有简历压到一页，全部项目、日期和指标都保留。
```

Expected behavior: keep the existing one-page template and QA gates, compress repetition first, and ask before removing facts or making an explicit two-page exception. Kami's two-page template must not be introduced implicitly.

## Evidence status

These are forward test prompts and expected decisions. No external provider run or recruiter blind review has been performed; those remain `missing evidence`.
