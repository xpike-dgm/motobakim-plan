# EVALUATION PROTOCOL

1. Manager onayli urun girdilerinden karar sorusunu, mandatory gate'leri ve ortak kriterleri cikarir.
2. Teknik iddialar mumkun oldugunca birincil/official kaynaklarla desteklenir; belirsizlik kanit gibi sunulmaz.
3. Manager karsilastirma ve ilk oneriyi `DRAFT / PROPOSED` olarak yazar.
4. Iki farkli AI/model ayni taslagi birbirlerinin cevabini gormeden bagimsiz ve adversarial olarak inceler:
   - Reviewer A: Architecture, Mobile & Scale,
   - Reviewer B: Security, Operations, Failure Modes & Cost.
5. Her bulgu severity, repo kaniti, bozulan invariant ve gerekli duzeltme/no-code kanit ihtiyaci ile kaydedilir.
6. Architect/Judge ortak noktalar, celiskiler ve manager cevabini sentezler; yeni kanit uydurmaz.
7. Kritik/major bulgular ya taslaga islenir ya da acik unresolved risk/soru olarak korunur.
8. Kullaniciya onerilen yon, alternatifler, trade-off'lar ve belirsizlikler birlikte sunulur.
9. Bu asamada kararlar `LOCKED` olmaz; kullanici karari sonrasi yalnizca Phase 5 ADR adaylari aktarilir.

## Review Independence Rule

Ilk turda reviewer'lar birbirlerinin cevabini ve Judge sentezini gormez. Reviewer ciktilari manager
tarafindan kisaltilip anlam degistirilerek gizlenmez; canonical review kayitlarinda bulgu, cevap ve
disposition ayri tutulur.

## Evidence Rule

Ozellik listesi, populerlik veya "tek codebase" tek basina karar kaniti degildir. En yuksek riskli Kavriva
senaryolari official dokuman, bilinen platform sinirlari, mimari walkthrough, failure table, capability/maintenance
evidence ve iki bagimsiz elestiriyle karsilastirilir. Kullanici karari geregi executable spike/prototype yazilmaz.
