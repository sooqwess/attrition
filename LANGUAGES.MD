# Language support

**Pack version:** 3.1.0

**Locales:** 69 · **Strings per locale:** 518 (`attrition.*`) plus 8
(`death.attack.attrition.*`)

Every locale is 100% filled — no empty strings, no missing keys, no broken
placeholders. This is verified on every build by `tools/checklang.py`.

Translations live in the **resource pack**, not the datapack. Without
`Attrition-RP-x.y.z.zip` the game shows everything in English.

---

## What is translated

Not only the interface:

- HUD, menus, tooltips and system messages
- **Custom mob names** — elites, elders, bosses
- **Custom item names and lore** — all 27 of them
- **Death messages** — the pack's own damage types
- The nine-page Field Manual

---

## Confidence tiers

Everything here was translated by hand, without machine translation services. But
one person cannot give 69 languages the same depth, so each locale carries an
honest label.

**Tier A — full manual translation (10 locales)**
Written line by line, keeping the rhythm and imagery of the English original.
Terminology cross-checked against Mojang's official translations.

**Tier B — manual regional adaptation (4 locales)**
Based on a neighbouring tier A locale and adapted by hand: forms of address,
regional vocabulary, spelling conventions. `es_ar` uses voseo, `pt_pt` uses *tu*
where `pt_br` uses *você*.

**Tier C — term canon plus proofread key strings (55 locales)**
A canon of roughly 52 recurring terms was written by hand and applied across the
file, with official Mojang names substituted from the vanilla locales — so an Ender
Pearl in a crafting hint is called what the player's inventory calls it. Individual
narrative lines may read plainly.

> Tier **C** locales are playable and terminologically consistent, but they have not
> been proofread by a native speaker. If you are a native speaker and you spot an
> awkward line, send a correction in [Issues](../../issues) — it will be applied
> with credit.

"Attrition" and "Sooqwess" are left in Latin script in every locale, including
those with non-Latin writing systems.

---

## Table

| Code | Language | Strings | Tier |
|---|---|---|---|
| `af_za` | Afrikaans | 518 | C |
| `ar_sa` | Arabic | 518 | C |
| `az_az` | Azerbaijani | 518 | C |
| `be_by` | Belarusian | 518 | C |
| `be_latn` | Belarusian (Latin) | 518 | C |
| `bg_bg` | Bulgarian | 518 | C |
| `bs_ba` | Bosnian | 518 | C |
| `ca_es` | Catalan | 518 | C |
| `cs_cz` | Czech | 518 | C |
| `cy_gb` | Welsh | 518 | C |
| `da_dk` | Danish | 518 | C |
| `de_de` | German | 518 | A |
| `el_gr` | Greek | 518 | C |
| `en_gb` | English (UK) | 518 | A |
| `en_us` | English (US) | 518 | A |
| `eo_uy` | Esperanto | 518 | C |
| `es_ar` | Spanish (Argentina) | 518 | B |
| `es_es` | Spanish (Spain) | 518 | A |
| `es_mx` | Spanish (Mexico) | 518 | B |
| `et_ee` | Estonian | 518 | C |
| `eu_es` | Basque | 518 | C |
| `fa_ir` | Persian | 518 | C |
| `fi_fi` | Finnish | 518 | C |
| `fil_ph` | Filipino | 518 | C |
| `fr_ca` | French (Canada) | 518 | B |
| `fr_fr` | French | 518 | A |
| `ga_ie` | Irish | 518 | C |
| `gl_es` | Galician | 518 | C |
| `he_il` | Hebrew | 518 | C |
| `hi_in` | Hindi | 518 | C |
| `hr_hr` | Croatian | 518 | C |
| `hu_hu` | Hungarian | 518 | C |
| `hy_am` | Armenian | 518 | C |
| `id_id` | Indonesian | 518 | C |
| `is_is` | Icelandic | 518 | C |
| `it_it` | Italian | 518 | A |
| `ja_jp` | Japanese | 518 | C |
| `ka_ge` | Georgian | 518 | C |
| `kk_kz` | Kazakh | 518 | C |
| `ko_kr` | Korean | 518 | C |
| `ky_kg` | Kyrgyz | 518 | C |
| `la_la` | Latin | 518 | C |
| `lt_lt` | Lithuanian | 518 | C |
| `lv_lv` | Latvian | 518 | C |
| `mk_mk` | Macedonian | 518 | C |
| `mn_mn` | Mongolian | 518 | C |
| `ms_my` | Malay | 518 | C |
| `nl_nl` | Dutch | 518 | C |
| `no_no` | Norwegian Bokmal | 518 | C |
| `pl_pl` | Polish | 518 | A |
| `pt_br` | Portuguese (Brazil) | 518 | A |
| `pt_pt` | Portuguese (Portugal) | 518 | B |
| `ro_ro` | Romanian | 518 | C |
| `ru_ru` | Russian | 518 | A |
| `sk_sk` | Slovak | 518 | C |
| `sl_si` | Slovenian | 518 | C |
| `sq_al` | Albanian | 518 | C |
| `sr_cs` | Serbian (Latin) | 518 | C |
| `sr_sp` | Serbian | 518 | C |
| `sv_se` | Swedish | 518 | C |
| `ta_in` | Tamil | 518 | C |
| `th_th` | Thai | 518 | C |
| `tr_tr` | Turkish | 518 | C |
| `tt_ru` | Tatar | 518 | C |
| `uk_ua` | Ukrainian | 518 | A |
| `uz_uz` | Uzbek | 518 | C |
| `vi_vn` | Vietnamese | 518 | C |
| `zh_cn` | Chinese (Simplified) | 518 | C |
| `zh_tw` | Chinese (Traditional) | 518 | C |
---

## Notes

- `ky_kg` (Kyrgyz) and `uz_uz` (Uzbek) do not exist in vanilla Minecraft, so there
  were no official Mojang names to draw terminology from. They were done entirely by
  hand and have no vanilla cross-check.
- Missing locales fall back to `en_us` **from this pack** before falling back to the
  component default, so a partially supported client never shows a raw translation
  key.
- Crafting hints deliberately avoid ingredient counts. A string like "2 paper +
  1 string" forces every language to agree with a numeral, which breaks grammar in
  Slavic, Arabic and Armenian among others. Hints name the cure; the recipe book
  carries the ingredients.

## Contributing a translation

1. Take `attrition-rp/assets/attrition/lang/en_us.json` as the source of truth.
2. Copy your locale's file and edit the values only — never the keys.
3. Keep `☃0☃`-style placeholders exactly as they appear, including order.
4. Open a pull request or attach the file to an issue.

Corrections to tier C locales are especially welcome, and are the fastest way to
promote a language to tier A.
