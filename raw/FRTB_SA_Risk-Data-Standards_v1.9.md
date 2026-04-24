ISDA Sfficient Markets

# ISDA FRTB-SA: RISK DATA STANDARDS

Version 1.8: 26 January 2024

# ISDA Safeient Markets

Contents   
Track changes 4   
1 Introduction .   
2 Common Risk Interchange Format (CRIF). 5   
3 Format overview ... . 6   
4 Fields description .. 8   
5 Variants description 12   
6 Variants examples.. ... 13   
6.1 Vega – Variants 1 & 2.. .... 13   
6.2 Curvature – Variants 1a & 2a 13   
6.3 DRC – Variants 1 & 2 . 14   
6.3.1 DRC_NS . . 14   
6.3.2 DRC_SNC . 14   
6.3.3 DRC_SC . 15   
7 RRAO example .. 16   
8 Fields guidance per risk type....... ...... 17   
8.1 GIRR_DELTA 17   
8.2 GIRR_VEGA.. 18   
8.3 GIRR_CURV... .. 18   
8.4 CSR_NS _DELTA.. 19   
8.5 CSR_NS _VEGA ... 19   
8.6 CSR_NS _CURV ... .. 20   
8.7 CSR_SNC _DELTA..   
8.8 CSR_SNC _VEGA . 21   
8.9 CSR_SNC _CURV .. 21   
8.10 CSR_SC _DELTA .. . 22   
8.11 CSR_SC _VEGA .. . 22   
8.12 CSR_SC _CURV . 23   
8.13 COMM _DELTA.....   
8.14 COMM _VEGA . ........ 24   
8.15 COMM _CURV. 24   
8.16 EQ_DELTA. 25   
8.17 EQ _VEGA . 25

ISDA Sfiecient CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION Markets

8.18 EQ _CURV . 26   
8.19 FX _DELTA 26   
8.20 FX _VEGA.. . 27   
8.21 FX _CURV.. 27   
8.22 DRC_NS . 28   
8.23 DRC_SNC . 29   
8.24 DRC_SC . . 30   
8.25 RRAO . 30   
9 CRIF files and ISDA ecosystem . . 32   
9.1 The CRIF file standard in ISDA FRTB-SA calculator and Unit Test .. . 32   
9.2 Controlling FRTB-SA calculations with configuration Flags.. . 32   
9.2.1 CRR2_RW_INFL_XCCY .. . 32   
9.2.2 VEGA_CORR_INFL_XCCY: .. . 32   
9.2.3 CSR_NS_INDX_BUCKET_NAME_CORRELATION.. . 33   
9.2.4 DRC_NS_COVERED_SENIORITY . 33   
9.2.5 CRR2_CSR_NS_INDX_RATING_CORR: ... . 33

10 References . 34

Table 1: RiskType options for SBM calculation . 8   
Table 2: RiskType options for DRC calculation.... 8   
Table 3: Risk Type options for RRAO.... ... 8   
Table 4: Qualifier field guidance .... . 9   
Table 5: Bucket field guidance ... 9   
Table 6: Label1 field guidance.... . 10   
Table 7: Label2 field guidance.... . 10   
Table 8: Input Variants.... .. 13   
Table 9: Vega Variants . 13   
Table 10: Curvature Variant 1a .... 13   
Table 11: Curvature Variant 2a . 14   
Table 12: DRC_NS Variant 1 (M2M).. ... 14   
Table 13: DRC_NS Variant 2 (JTD) . . 14   
Table 14: DRC_NS Variant 2 (JTD) . . 14   
Table 15: DRC_SNC Variant 1. . 15   
Table 16: DRC_SNC Variant 2.. . 15   
Table 17: DRC_SC Variant 1 (Banking Book approach) .. .. 15   
Table 18: DRC_SC Variant 2 (Decomposition approach) . . 16   
Table 19: RRAO example.. 16

# ISDA Sfieient Markets

Table 20: Field Guidance - General Fields. 17   
Table 21: Field Guidance - GIRR Delta .. . 17   
Table 22: Field Guidance - GIRR Vega .... .. 18   
Table 23: Field Guidance - GIRR Curvature... ... 19   
Table 24: Field Guidance - CSR_NS Delta..... ... 19   
Table 25: Field Guidance - CSR_NS Vega ... ... 20   
Table 26: Field guidance - CSR_NS  Curvature ... .. 20   
Table 27: Field Guidance - CSR_SNC  Delta.. .. 21   
Table 28: Field Guidance - CSR_SNC Vega .. .. 21   
Table 29: Field Guidance - CSR_SNC Curvature ...... .... 22   
Table 30: Field Guidance - CSR_SC Delta ... .. 22   
Table 31: Field Guidance - CSR_SC Vega.. .. 23   
Table 32: Field Guidance - CSR_SC Curvature..... . 23   
Table 33: Field Guidance - Commodity Delta ..... .. 24   
Table 34: Field Guidance - Commodity Vega .... ... 24   
Table 35: Field Guidance - Commodity Curvature ..................... ..... 25   
Table 36: Field Guidance - Equity Delta .... .. 25   
Table 37: Field Guidance - Equity Vega.. .. 26   
Table 38: Field Guidance - Equity Curvature.... .. 26   
Table 39: Field Guidance - FX Delta .. .. 27   
Table 40: Field Guidance - FX Vega ...... .... 27   
Table 41: Field Guidance - FX Curvature.... ... 28   
Table 42: Field Guidance - DRC_NS.. .. 29   
Table 43: Field Guidance - DRC_SNC . . 29   
Table 44: Field Guidance - DRC_SC . 30   
Table 45: Field Guidance – RRAO.. .. 31

# ISDA Safeient Markets

Track changes   
![](images/f19b919c1847e7b6ad4cf8fce00cf2088583d9b81ffe5f6cbfb5d0521f50167b.jpg)

# ISDA Stfieient Markets

# 1 Introduction

Basel Committee has revised the market risk framework for calculation of minimal capital requirements for market risk, with the latest standard published on December 2019, see [0]. This revision called Fundamental Review of the Trading Book (FRTB) produced a new and more risk sensitive Standardised approach (SA). As a response ISDA launched an industry wide benchmarking exercise to help measure and hopefully decrease the degree of variability in the implementation of the FRTB-SA model. The process requires exchange of risk data for a number of benchmark portfolios, between participating institutions and ISDA. Therefore, a structured and standardised format to transmit such data was developed.

This document sets complete standards and describes the data format used for data exchange and risk calculations, giving additional descriptions and clarifications of the various risk factors and other inputs, as well as worked examples.

As part of that, the document also proposes a common standard for interchange of FRTB SA risk between participants and others.

# 2 Common Risk Interchange Format (CRIF)

There is a strong need for a common way of describing risk on portfolios and trades. This is required by market participants for a number of use cases of which a non-exhaustive list can be found below.

Third party vendors which aim to provide FRTB reconciliation or management services. ISDA member firms for back-testing, benchmarking and other validation processes. New firms can be benefited by having a swift and precise on-boarding phase related to the FRTBSA regulatory capital methodology.

The proposal is for a simple, robust format, which can be read by automated processes as well as being capable of manual inspection. The format is specified for the current set of risk factors, but can also easily be extended to handle new risk factors in future.

The objective is to have a format which is capable of achieving two different objectives – both risk reconciliation and the basis for regulatory capital calculation. Given risk data in this format, it should be straightforward and mechanical to calculate the regulatory capital of a portfolio, using only additional information from the FRTB Methodology document, [0].

# ISDA Stfieient Markets

# 3 Format overview

The format can be implemented as an Excel file or in any other column based file extension like csv or txt, with defined data fields arranged in columns. Elements can be either textual (string), date or numerical and type can be context-dependent.

The first row of the Excel file contains the header with the names of the columns.

Each additional row contains a single risk factor for a trade or portfolio.

Below we provide a quick overview of each column. For more details see $^ { \prime \prime } 4$ . Fields description”.

1. Portfolio ID - string describing portfolio ID.   
2. Trade ID – string describing the trade ID.   
3. Variant - string describing the variant of the input format. This string is only relevant for Vega, Curvature and DRC1.   
4. Sensitivity ID - string describing the risk factor ID.   
5. RiskType – string describing the risk factor type, such as general interest-rate risk (GIRR), nonsecuritisations credit risk, etc. Specific examples include GIRR_DELTA (interest-rate delta), FX_DELTA (FX delta risk), and others2.   
6. Qualifier – string description of the particular risk factor. Depends on the RiskType. For example for GIRR, the Qualifier denotes the ISO currency code of  and issuer name in case of equities   
7. Bucket – Denotes the FRTB-SA bucket as per the regulations. For GIRR, FX denotes the integer code relating to liquidity category: 1- Regular, 2- Liquid of currency name of the Qualifier we are trying to model. Exact meaning, interpretation depends on RiskType3.   
8. Label1 – additional qualifier, typically describing the tenor of an Option (for vega RiskTypes) or the shift necessary to calculate CVR (for curvature RiskTypes).   
9. Label2 – additional qualifier used to further specify the type of risk factor within the row. Meaning depends on the RiskType.   
10. Amount – amount of the risk, in units of a given currency. Number format. Can have different meaning based on RiskType or Variant. For example, in the case of RRAO it is the Notional of the position.   
11. AmountCurrency – currency of the “Amount” field. Should be a standard three-letter ISO currency code.   
12. AmountUSD – amount of the risk, expressed in USD.  (This has the additional benefit of implying the effective FX rate used by the data-producer to convert between the amount currency and USD.)

Additional columns:

13. Label3 – used to input volatility for vega risk for all risk types or notional for calculating DRC for DRC_NS risk type for ‘Variant ${ \bf \Omega } ^ { 1 ^ { \prime } }$ . For all other positions it is blank.   
14. EndDate – is a maturity date for credit instruments and is used only for DRC. The date must be entered in “YYYY-MM-DD” format, according to the ISO 8601 standard. For other non-relevant positions it must remain blank.

# ISDA Stfieient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

15. CreditQuality – is either an issuer rating class for credit instruments or a direct risk-weight input. Depending on the jurisdiction it can follow a standard Moody’s rating nomenclature, e.g. “AAA”, or Credit Quality Step (CQS) nomenclature etc. For other irrelevant positions it must remain blank.

16. LongShortInd – Long or Short indicator. It is used only for DRC calculation for credit instruments. It must take either “L”, $" \mathsf { S } ^ { \prime \prime }$ or blank for irrelevant positions.

17. CoveredBondInd – takes values, $" \boldsymbol { \gamma } \prime \prime$ for yes, $" \mathsf { N } ^ { \prime \prime }$ for no and blank if not relevant. The field applies only to calculation of DRC for credit instruments which are non-securitisations.

18. TrancheThickness – is a number between 0 and 1 and is used for DRC calculation for Securitisation non-CTP positions under Variant 1. It is used for the calculation of the relevant risk-weights based on the SEC-ERBA methodology.

# ISDA Sfieient Markets

# 4 Fields description

Where dates are used in CRIF files, they should be formatted according to the ISO 8601 standard, which can be described as “YYYY-MM-DD”, so that 1 September 2016 would be “2016-09-01”. This format is unambiguous, and has useful sorting properties.

Below we give a detailed description of the various fields:

RiskType: String denoting the FRTB-SA risk class and risk combination for the Sensitivity Based Method (SBM) related calculations. Alternative options provided for the Default Risk Charge (DRC) specification.

![](images/266dbf8da9772dec03b8dc22bf34878ac3e4a91466b54d0e1625978093521da3.jpg)
Table 1: RiskType options for SBM calculation

![](images/366bc2427bca520429a6daec719a58d81f8228463e66c4c6d239d2c91f383b50.jpg)
Table 2: RiskType options for DRC calculation

![](images/9ebf55ead8d5d3859a5bfe0b54320c42f9fb31ec2ba57af301bdaff7fb5a3b24.jpg)
Table 3: Risk Type options for RRAO

Qualifier: String denoting the risk factor at an “in-bucket” level.

![](images/8e69973bb56babef7e4d3febbac040ed9f9ef4890e32adfb79d98349d54809ff.jpg)

# ISDA Sfieient Markets

![](images/fc6d695f6dcf568c3122d738411c04027a6a025985ec8f0568682d9b5edc27bb.jpg)
Table 4: Qualifier field guidance

Bucket: This field typically denotes the Bucket the particular sensitivity belongs to but its actual meaning depends on the RiskType it is used with:

Label1: This field has different meanings depending on the RiskType it is used with:   
![](images/f5523e1255d2af50012643a1accc5aa6ea3b90675e8516c854cdaa7bb6bef5b7.jpg)
Table 5: Bucket field guidance

![](images/bd20000c6c306d6c87f25c98924884f133e0ca90c8fd0185e0f45fd6cb4826cb.jpg)

# ISDA Sfieient Markets

Label2: This field has different meanings depending on the RiskType it is used with:   
![](images/f7a02cf066c4a25dedafbd5cc13b7be2d2c6fec8bfe020f3c453201c20b71592.jpg)
Table 6: Label1 field guidance

![](images/e8a70e64f51dd956e6d6415fbddad8dde9c267bc3279f914990bb7c070b4015a.jpg)
Table 7: Label2 field guidance

Label3: This field has different meanings depending on the RiskType it is used with:

GIRR_VEGA, CSR_NS_VEGA, CSR_SNC_VEGA, CSR_SC_VEGA, EQ_VEGA, COMM_VEGA, FX_VEGA.   
When Variant2 is used7, Label3 is used to denote the implied volatility of the option.

# ISDA Stfieient Markets

DRC_NS: Notional for Variant 1. Negative amount signifies a short (in the DRC sense) position.   
Not required for Variants 2 and 3.   
Otherwise: <blank>.

EndDate: Maturity date or option expiry in ISO-Standard "YYYY-MM-DD". Applies to below RiskTypes (otherwise <blank>):

DRC_NS (except from Variant 3)   
DRC_SNC   
DRC_SC

It is used to scale DRC positions according to maturity assuming an ACT/365  day-count convention.

CreditQuality: Issuer’s credit quality for example “AAA” for Basel ruleset and $^ { \prime \prime } { \mathsf { C } } { \mathsf { O } } { \mathsf { S } } 1 ^ { \prime \prime }$ for CRR ruleset. Applies to RiskTypes (otherwise <blank>). In some cases we use the risk-weight as a direct input for example in DRC_SNC Variant 2 and DRC_SC Variant 1 (Banking Book approach):

CSR_NS_DELTA   
CSR_NS_CURV   
DRC_NS,   
DRC_SNC,   
DRC_SC

LongShortInd: “L” (long) or $^ { \prime \prime } { \sf S } ^ { \prime \prime }$ (short) indicator. Applies to DRC RiskTypes, DRC_NS, DRC_NS, DRC_SNC, DRC_SNC, DRC_SC, DRC_SC. Blank otherwise.

CoveredBondInd: Boolean. “Y” or <blank>. Applies only to DRC_NS risk type.

TrancheThickness: Number between 0 and 1 describing the tranche thickness. Applies to the DRC_SNC Variant 1 (SEC-ERBA).

Amount: This field has different meanings depending on the RiskType it is used with. It is always a float.   
For more information see Table 8: Input Variants.

AmountCurrency: The currency of the value under the Amount column

AmountUSD: Amount equivalent expressed in USD.

# ISDA Stfieient Markets

# 5 Variants description

Since the infrastructure developed for calculation of standardised capital for market risk varies among banks, various input variants are permissible. These variants are equivalent ways to describe the inputs that correspond to a specific risk calculation and they constitute valid data formats that are described in the Table below. In certain cases, Variants are used to model different calculation methods permissible by the rules.

![](images/c5cf0083123702a91b7a0002915a9b1d7001619865a84ef0dee616f2c9df2e82.jpg)

# ISDA Sfecient Markets

![](images/20c27e8070dc56ae26764628b5f564fc7389c19ac285f80d2ab06dda67e0c5d8.jpg)
Table 8: Input Variants

# 6 Variants examples

# 6.1 Vega – Variants 1 & 2

The “Amount” for “Variant ${ 1 ^ { \prime \prime } }$ is the “vega risk sensitivity to a given risk factor”8. This sensitivity $s _ { k }$ is an input to the model and according to the regulations it is calculated as such:

$$
s _ { k } = v e g a \times i m p l i e d \ v o l a t i l i t y
$$

Therefore, in the example from the table below, “Variant $1 ^ { \prime \prime }$ directly inputs $s _ { k } = - 1 0 0$ into the model.

However, some banks prefer to input instead the 𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣 and 𝑚𝑚𝑚𝑚𝑚𝑚𝑚𝑚𝑚𝑚𝑚𝑚 𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣 separately and leave the model itself to calculate $s _ { k }$ . Such banks will use “Variant $2 ^ { \prime \prime }$ where the “Amount” denotes the 𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣 and “Label3” denotes the 𝑖𝑖𝑖𝑖𝑖𝑖𝑖𝑖𝑖𝑖𝑖𝑖𝑖𝑖 𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣𝑣 and therefore $s _ { k } = - 1 0 0 = - 4 0 0 \times 0 . 2 5$ .

![](images/fc0f1e0202a454a3ed7b06c093c2e22830b2e3019be099acc33b7571f139aaee.jpg)
Table 9: Vega Variants

# 6.2 Curvature – Variants 1a & 2a

As described in MAR21.5 the inputs for the calculation of FRTB-SA Curvature metrics is a set of values called $C V R ^ { + }$ and $C V R ^ { - }$ . Roughly speaking these correspond to the change in the value of an instrument when the underlying risk factor is bumped upwards $( C V R ^ { + } )$ or downwards $( C V R ^ { - } )$ , minus the impact of the first order movement (delta impact). For an exact specification see MAR21.5.

We start the description of the curvature Variants by the simplest one.

# 1. Variant 1a (Full revaluation – delta stripped)9

Under this Variant the values under “Amount” represent the $C V R ^ { + }$ and $C V R ^ { - }$ respectively for a change of $\pm 0 . 5 5$ of the underlying risk factor (see under “Label1”). Every “Sensitivity $| \mathsf { D } ^ { \prime \prime }$ needs two rows as entries.

![](images/fb5afbb040e54ab5435343fc0031680c331b896a12795c950a1254d3df4fe48a.jpg)
Table 10: Curvature Variant 1a

# 2. Variant 2a (Full revaluation)

# ISDA Safeient Markets

This Variant is similar to “Variant $2 \boldsymbol { \mathrm { b } } ^ { \prime \prime }$ but the 𝐶𝐶𝐶𝐶𝐶𝐶 values in the last two rows are not “deltastripped” i.e. the impact of delta in the calculation of 𝐶𝐶𝐶𝐶𝐶𝐶s has not been removed yet. The delta impact is represented in the first row under “Amount” per $0 . 0 1 \%$ change of the risk factor (“Label1”). Based on this information we can recover the $C V R s$ from “Variant1a”. This operation happens behind the scenes, within the FRTB-SA engine. For example:

$$
C V R _ { 2 b } ^ { + } = 3 7 , 8 2 0 = - ( 3 9 , 1 9 5 - 2 5 * { \frac { 0 . 5 5 } { 0 . 0 1 } } )
$$

![](images/d17c92b5434ac20ad18d7c3f5e16a7ea592b48b6d7d7f8355cc8f3435b271290.jpg)
Table 11: Curvature Variant 2a

# 6.3 DRC – Variants 1 & 2

# 6.3.1 DRC_NS

# 1. Variant 1 (Marked to Market)

This Variant is defined by using the values under “Amount” as the Market Value (Marked-to-Market) of the instrument, while “Label3” is the associate Notional. The Gross Jump-To-Default (JTD) can be calculated by the engine using the regulatorily prescribed formulas.

![](images/46bbd3f3a5ada8b64c78ddef3c6e5bc20854ed60de83a4b53170cfba8ab10a60.jpg)
Table 12: DRC_NS Variant 1 (M2M)

# 2. Variant 2 (JTD)

For this Variant, the value under “Amount” is the actual Jump-To-Default (JTD) value associated with the seniority class of the exposure, specified under columns Label2. For example for a “SENIOR” exposure the model will apply an recovery rate of $2 5 \%$ according to the regulations. The value under Amount is “maturity unscaled” and is scaled by the model according to the maturity of the exposure (defined under column “EndDate”).

![](images/259e5380e02a489fb0fee48aed0b514937ec3cbfa3bb5d468539eb04a01cd9cb.jpg)
Table 13: DRC_NS Variant 2 (JTD)

# 3. Variant 3 (Maturity Scaled JTD)

This is the same as Variant 2 above but this time the value under Amount is already maturity scaled by the user. There is no need to provide the maturity under the EndDate column.

![](images/4323c7f9aa84042826eccc9a59d94353ea30a640d4c4608909c28ad31c77a99a.jpg)
Table 14: DRC_NS Variant 2 (JTD)

# 6.3.2 DRC_SNC

# 1. Variant 1 (SEC-ERBA)

# ISDA Safeient Markets

This Variant leverages the credit rating found under the CreditQuality column, and uses the SECERBA methodology to calculate the risk-weights needed to calculate the DRC capital. The value under the “Amount” column is the JTD which according to the rules (see MAR22.27) is the same as the market value of the position. TrancheThickness also plays a role to scale the risk-weight according to the SEC-ERBA methodology. Finally, Label2 entries are used to define a SENIOR or NONSENIOR position.

Since, SEC-ERBA is not supported by the US-NPR rules, Variant 1 should not be used with it. It can be used with all other jurisdictions.

![](images/e154e17c2025448edba58f166dc131523321bf7061fb4124e43dd29b7814f87c.jpg)
Table 15: DRC_SNC Variant 1

# 2. Variant 2 (risk-weight as an input)

Similarly to Variant 1, the value under the “Amount” column is the JTD which according to the rules (see MAR22.27) is the same as the market value of the position. However, unlike Variant 1, we do not make any assumption about the feeder model that is used to calculate the risk-weights. The user inputs the risk-weights directly under the CreditQuality column. The risk-weight must be input as a float number and not as a percentage10. Since SEC-ERBA is not used, Label2 and TrancheThickness columns can be left empty. This Variant is applicable to all jurisdictions and can be used to model the Expanded and Standardised calculations under the US-NPR if required.

![](images/0fdeba8d66509bba667a0722ecf957193350da1caae1eb9d6cb1c3353a0f95b4.jpg)
Table 16: DRC_SNC Variant 2

# 6.3.3 DRC_SC

# 1. Variant 1 (Banking Book approach)

In this Variant each row reports the JTD number under the “Amount” column. Under the CreditQuality column the user can input the risk-weights they have calculated using the relevant Banking-Book model. Label2 entries11 are used to denote the type of exposure being modelled. The Bucket is used to denote the relevant DRC_SC bucket (usually the index the tranche belongs to) and Qualifier the tranche’s series.

![](images/596b188227032ffc294036704d724cf2d980c5dde8696014bc1d41fb545c7e4e.jpg)
Table 17: DRC_SC Variant 1 (Banking Book approach)

# ISDA Sfecient Markets

# 2. Variant 2 (Decomposition approach)

Variant 2 is similar to Variant 1 but in this case it is assumed that the tranched indices have been decomposed to single names according to the relevant regulatorily described rules. In this case, the riskweight determination can be done using the credit rating under the CreditQuality column and the relevant DRC_NS rules.

![](images/388049be5cd34483a20347ce65bad3ad7baf5fd4fe44df7811d4af17f9a267fd.jpg)
Table 18: DRC_SC Variant 2 (Decomposition approach)

# 7 RRAO example

RRAO is specified in CRIF by providing the positions Notional under the Amount and AmountUSD columns. The correct risk weight is applied based on the entry under RiskType. “RRAO_1_PERCENT” is used to model positions with exotic underlyings ( $1 \%$ risk weight) while “RRAO_01_PERCENT” is used for instruments with other residual risks ( $0 . 1 \%$ risk weight).

![](images/985ffa9bfd6671d4df76a96296b490471ea7e891affff785089ff4f8bb943e32.jpg)
Table 19: RRAO example

# ISDA Sfieient Markets

# 8 Fields guidance per risk type

The following session provides guidance for each CRIF field, depending on Risk Type and Jurisdiction12 (rule-set). The table below presents some fields that pertain to all Risk Types, namely Portfolio ID and Trade ID.

![](images/cd21a8b5ea1e95e32c3db7cb148bec5ce0b896acfbb960b03a5cf8ff74692bf2.jpg)
Table 20: Field Guidance - General Fields

The following subsections will examine in more detail each individual Risk Type and the corresponding Field types.

# 8.1 GIRR_DELTA

Table 21: Field Guidance - GIRR Delta   
![](images/d57a2e703d7fb46c9a224f80f74360717927bc5abcc73d6499a726cf16f46820.jpg)

GIRR_Tenors $\mathbf { \tau } = \mathbf { \tau }$ {0.25, 0.5, 1, 2, 3, 5, 10, 15, 20, 30, “INFL”, “XCCY”}

# ISDA Sfieient Markets

# 8.2 GIRR_VEGA

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

Table 22: Field Guidance - GIRR Vega   
![](images/1315d02d365817528e0ba38947938cbd78ea21f318ce9ea8d9f6dbce3b7516e0.jpg)

GIRR_Tenors $\mathbf { \tau } = \mathbf { \tau }$ {0.25, 0.5, 1, 2, 3, 5, 10, 15, 20, 30, “INFL”, “XCCY”}

GIRR_option_tenors $\mathbf { \tau } = \mathbf { \tau }$ {0.5, 1, 3, 5, 10}

# 8.3 GIRR_CURV

![](images/a2d5f301829f2fbc6529edee7ae480c11b4920a092a94ce9034db87f61f843a0.jpg)

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

Table 23: Field Guidance - GIRR Curvature   
![](images/e13645bf7d9963392c7590c6b72164bfe2bc1287ffe36f69ec6b7dcc82e61de1.jpg)

# 8.4 CSR_NS _DELTA

![](images/4ec5470aafca6b0c7a7f4d1b8464c22adc2117b9549feed3450e88b6c9af06d8.jpg)
Table 24: Field Guidance - CSR_NS Delta

CSR_tenor $= \{ 0 . \}$ 5, 1, 3, 5 ,10}

# 8.5 CSR_NS _VEGA

![](images/de19b0974ead74c870e6c04289968af02cd6fa9a22ead094642a50445db5634a.jpg)

# ISDA Sfieient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

![](images/ec6394e2ab092c28caffef8a56567a1c931e8b6fabd89e9059d0b69f818ee0cf.jpg)
Table 25: Field Guidance - CSR_NS Vega

# 8.6 CSR_NS _CURV

![](images/3fddc133e70c51473519776c2fee5d09a17fd18f435bee160183d9c8f13cf73a.jpg)
Table 26: Field guidance - CSR_NS  Curvature

# 8.7 CSR_SNC _DELTA

![](images/5dab4aeeaf96ea63f910a0985b5ee352ca278c2e09b63fbd49a19033a51b8b50.jpg)

# ISDA Safeient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

![](images/aaba8fc39269159ce7be847f9d8174fba0aceaad0d6b0885e526b1cca432397d.jpg)
Table 27: Field Guidance - CSR_SNC  Delta

# 8.8 CSR_SNC _VEGA

![](images/8f3d8efc3dcb3614b770d42936ffdb33db3c285639790aad94f3d0820ef0824c.jpg)
Table 28: Field Guidance - CSR_SNC Vega

# 8.9 CSR_SNC _CURV

![](images/74b8b0e5a46f01dfdddc79cca326396e6492bb8d1aa14f703a4c93090d7ef292.jpg)

# ISDA Sfiecient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

![](images/a6214c1337e50267d7a0b5a27e76dbe5c92e5683d10f80dde17f2136a21c22e7.jpg)
Table 29: Field Guidance - CSR_SNC Curvature

# 8.10 CSR_SC _DELTA

Table 30: Field Guidance - CSR_SC Delta   
![](images/3c173b0c5b62c824f74de569cf8c1390ec3a76f1d7aae7e11b2898accbf13b1d.jpg)

# 8.11 CSR_SC _VEGA

![](images/6eb2628881937a1aed9c4b36d6bd064451db071f0398eb53671fd231d625a926.jpg)

# ISDA Sfiecient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

Table 31: Field Guidance - CSR_SC Vega   
![](images/0dd34d5407ee81d0cc655a5f3b0ebd095b106b469a8594fdd2cf51feeb29e70e.jpg)

# 8.12 CSR_SC _CURV

![](images/25207052c9ec282ed4238355a947830964e1db2a18daf8934c5bbb0092f06c15.jpg)
Table 32: Field Guidance - CSR_SC Curvature

# 8.13 COMM _DELTA

![](images/45fff9734d9a4e5c4c92c8419ff2239e20450f21f521c14a846492b68caaab4d.jpg)

# ISDA Sfieient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

Table 33: Field Guidance - Commodity Delta   
![](images/5512551e79c2a987fb32e2d2bc0deb3806722557e2c8817767fc34021bd4c6c9.jpg)

# 8.14 COMM _VEGA

Table 34: Field Guidance - Commodity Vega   
![](images/fe1d050c91dd2e9b05f753b7d6f1d1ebc4b628720bc9ae58c14a2de7dcb78f75.jpg)

# 8.15 COMM _CURV

![](images/3bf7d579f648da5804ec76a12c40ed90f1f9473e1ca0c25c04ad8b475e010f27.jpg)

# ISDA Sfieient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

Table 35: Field Guidance - Commodity Curvature   
![](images/99353980df4493e0e7123acf748bfa7867ad284464ffd19e4a181c551936eda6.jpg)

# 8.16 EQ_DELTA

![](images/65677aa779f2742b1c97d93514a9b6274fbf5489180552e8de73be4f4815d427.jpg)
Table 36: Field Guidance - Equity Delta

# 8.17 EQ _VEGA

![](images/a5bb401d4cd2d546132dd4bab5be6d7ea5573c8de04df5d3483b37c2ea9ae880.jpg)

# ISDA Sfieient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

Table 37: Field Guidance - Equity Vega   
![](images/601438decd8830087405e0ed48705d6f4ac5cc813557df8271194500fc9c68d6.jpg)

# 8.18 EQ _CURV

Table 38: Field Guidance - Equity Curvature   
![](images/7ef3c70dc8137e5ba848257b0100e920271d58f8b6431d30d95a5587d98a072c.jpg)

# 8.19 FX _DELTA

![](images/1eee997991da88607bf77e88496c45108b91460b006276cc5779925ee9709db7.jpg)

# ISDA Sfiecient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

![](images/51f0a25b1964738be33f9eded2c0bc7af7c67acab56d95ed2a14ed87523d41a9.jpg)
Table 39: Field Guidance - FX Delta

8.20 FX _VEGA   
![](images/887503f88ffd0c383936b6fcc845b850fffa1ed2b5056f3d3179a497221914f2.jpg)

FX_Option_Tenors $= \{ 0 . 5 , 1 , 3 , 5 , 1 0 \}$

# 8.21 FX _CURV

Table 40: Field Guidance - FX Vega   
![](images/0dce439f4392d48904c538fc88e8fa28421d2a4086bffe352717a1df6e9eda7e.jpg)

# ISDA Sfieient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

![](images/97094a71d9c292f5968d69f095fe4db40b56e3eb675c8555c83c7881825c76cb.jpg)
Table 41: Field Guidance - FX Curvature

8.22 DRC_NS   
![](images/0cc52bf577a67d131ce5cd0708ea1ed44c14e9dff23339b0b8865795122a9c71.jpg)
17 1 corresponds to illiquid and 2 to liquid i.e. divide the risk-weight by the $\sqrt { 2 }$ 18 3,4 and 5 are relevant to CRR2 and the risk-weights that apply to the ERMII currencies, ref Article 325av (2)(3)(5).

# ISDA Safeient Markets

![](images/9d9c7822975521eb3fc879a1e4aed4b24306b13b7b18f49871520bf200c6178d.jpg)
Table 42: Field Guidance - DRC_NS

# 8.23 DRC_SNC

![](images/d05cefa7625362542c95cc5462628dbafc9f7c3b541d0eadfcda5bcc395ba5c8.jpg)
Table 43: Field Guidance - DRC_SNC

# ISDA Sfecient Markets

Variant 1 corresponds to SEC-ERBA approach for calculating risk-weights. Variant 1 does not apply to USNPR jurisdiction. Variant 2 to risk-weights as an input. See CreditQuality column.

8.24 DRC_SC   
![](images/cef4a104cbcae40c212bf0c74a901c2fcc8ab0e544a1b653b2fc8a50f883dab2.jpg)

Variant 1 corresponds to banking book approach where the risk-weights are direct inputs in the CreditQuality column. Variant 2 corresponds to decomposition approach where the assumption is that we can source the risk-weights using the DRC Non-Securitisation rules.

Table 44: Field Guidance - DRC_SC   
8.25 RRAO   
![](images/6139d157345f3dff51819cc74f07ae205e7ab983824758d29675c8ba1fa68dc9.jpg)

# ISDA Sfieient Markets

# CONFIDENTIAL NOT FOR FURTHER DISTRIBUTION

![](images/2b5ed6d07221c05ccfeca265296eb84d4ae3ef5bdc8d84f9b9f71d471ca0062a.jpg)
Table 45: Field Guidance – RRAO

# ISDA Safeient Markets

# 9 CRIF files and ISDA ecosystem

# 9.1 The CRIF file standard in ISDA FRTB-SA calculator and Unit Test

ISDA has built an ecosystem of tools around the CRIF standard in order to enhance our solutions suite. We have developed the FRTB-SA Unit Test which has been validated by numerous markets participants and constitutes the industry’s golden standard in regards to validating FRTB-SA implementations.

Furthermore, ISDA developed its own implementation of an FRTB-SA calculator which can be accessed through our online platform Perun©. Both these tools are built around the CRIF representation of FRTBSA inputs and are compatible with it. For example, interested users can upload CRIF files in Perun and calculate  FRTB-SA capital.

# 9.2 Controlling FRTB-SA calculations with configuration Flags

Our commitment to regulatory compliance and adaptability is reflected in our capability to interpret CRIF files across a spectrum of regulatory jurisdictions. We amplify this by integrating numerous configuration flags within the CRIF files.

These configuration flags align with the currently supported regulatory frameworks specifically:

MAR from Basel Committee on Banking Supervision (BCBS) European Union’s Capital Requirements Regulation (CRR2), and; UK's Prudential Regulation Authority (PRA) regulations.

The configuration flags act as dynamic parameters in risk calculations. Each flag represents an alternative interpretation or application of capital requirement rules, offering a nuanced approach to adjusting risk evaluations to match specific regulatory standards.

Specifically, the list of configuration flags includes:

# 9.2.1 CRR2_RW_INFL_XCCY

This configuration flag is associated with the interpretation of cross-currency (XCCY) and inflation (INFL) risk weights under the CRR2 regulations for liquid currencies. There are two alternatives:

Alt1: INFL and XCCY risk factor risk weights for liquid currencies are divided by $\sqrt { 2 }$ .

Alt2: CRR2 Article 325ae (3) can be read so as to imply that GIRR DELTA XCCY and INFL are not risk-free tenors and hence the RW division by $\sqrt { 2 }$ does not apply to them.

9.2.2 VEGA_CORR_INFL_XCCY:

This flag presents alternatives for calculating the GIRR Vega intra-bucket correlation for inflation (INFL) and cross-currency (XCCY) risks.

Alt 1: Follows the rules as described in MAR21.93 and MAR21.94. Specifically for ρoption_maturity:

$$
\begin{array} { r l } { \cdot } & { { } \mathsf { \rho } _ { \mathsf { N C C Y , N F L } } = 0 } \\ { \cdot } & { { } \mathsf { \rho } _ { \mathsf { P x c c Y , i } } = 0 } \\ { \cdot } & { { } \mathsf { \rho } _ { \mathsf { N N F L , i } } = 0 . 4 } \end{array}
$$

Alt 2: the correlation ρoption_maturity $= 1$ for all cases $( \rho _ { \mathsf { X C C Y , i } } = 1$ and $\rho _ { \mathsf { I F N L , i } } = 1 .$ .

# ISDA Stfieient Markets

Alt3: the formula in MAR21.93 for ρoption_maturity is used but an underlying maturity of 0.5 years is used for the INFL and XCCY tenors $U _ { \sf I N F L } = 0 . 5$ and $\mathsf { T } _ { \mathsf { X C C Y } } = 0 . 5 ^ { \prime }$ ).

Assumption 1 presents three alternatives. In the first one, correlations are determined based on the factors' characteristics, following MAR21.94. The second alternative sets a correlation of 1 for all combinations, while the third uses the formula in MAR21.93 with an underlying maturity of 0.5 years used in all cases.

# 9.2.3 CSR_NS_INDX_BUCKET_NAME_CORRELATION

Under Basel, as per MAR21.55 the name correlation applied within the index buckets 17 and 18 is set to be $\rho _ { \mathrm { n a m e } } = 8 0 \%$ .

However, under CRR2, as per Article 325ai the name correlation applied within the index buckets 19 and 20 is set to be the same as within any other buckets i.e. $\rho _ { \mathrm { n a m e } } = 3 5 \%$ .

The above gap has not been fixed by the EU regulator as part of the Jan 2020 DA. It appears that the regulator is aware but they didn't have the mandate to fix it. Therefore:

Alt 1: $\rho _ { \mathsf { n a m e } } = 3 5 \%$ for buckets 19 and 20 under CRR2. This is in line with the current CRR2 regulation.

Alt 2: $\rho _ { \mathrm { n a m e } } = 8 0 \%$ for buckets 19 and 20 under CRR2. This is in line with the expectation that the relevant gap between Basel and CRR2 will be bridged.

UK-PRA follows the Alt2 convention i.e. the applied $\rho _ { \mathsf { n a m e } } = 8 0 \%$ .

# 9.2.4 DRC_NS_COVERED_SENIORITY

This flag relates to how "covered" bonds are treated in default risk charge (DRC) calculations for nonsecuritisations. Alternative 1 adjusts the loss given default (LGD) of the exposure to 0.25, with the bond belonging to the seniority class specified under Label2. Alternative 2 treats "covered" bonds as a separate seniority class, ranked as EQUITY $\mathbf { \bar { \rho } } _ { < }$ NON-SENIOR $\mathbf { \bar { \rho } } _ { < }$ SENIOR $\rvert <$ COVERED:

Alt 1: "Covered" bond entry (see CoveredBondInd column) overrides the LGD of the exposure with 0.25.   
The exposure belongs to the seniority class specified under Label2.

Alt2: "Covered" bond is considered as a separate seniority class with seniority level as EQUITY $\angle$ NONSENIOR $\angle$ SENIOR $\angle$ COVERED.

# 9.2.5 CRR2_CSR_NS_INDX_RATING_CORR:

This flag is applicable only to CRR2 ruleset and for Credit Spread Risk (CSR) Non-Securitisation (NS) Index Buckets.

The inter-bucket γrating correlation that is applicable for the two CSR NS index buckets, is a point of divergence between the Basel and CRR2 implementations.

Specifically Basel suggests that this correlation should be 1 while Article 325j of CRR2 and UK-PRA CP specify that it should be 0.5.

We have therefore introduced two alternatives for the CRR2 calculation:

# ISDA Stfieient Markets

Alt 1: $\gamma _ { \mathrm { r a t i n g } } = 0 . 5$ thus $\gamma = \left( \gamma _ { \mathrm { r a t i n g } } * \gamma _ { \mathrm { s e c t o r } } \right) = 0 . 5 * 0 . 7 5 = 0 . 3 7 5$

Alt 2: $\mathtt { \mathtt { V r a t i n g } } = 1$ thus $\gamma = \left( \gamma _ { \mathrm { r a t i n g } } \ast \gamma _ { \mathrm { s e c t o r } } \right) = 1 \ ^ { \ast } \ 0 . 7 5 = 0 . 7 5$

UK-PRA follows the Alt1 convention i.e. the applied $\gamma _ { \mathrm { r a t i n g } } = 0 . 5$ .

# 10 References

Basel Committee on Banking Supervision (BCBS). (2019, December 15). MAR - Calculation of RWA for market risk. Retrieved from https://www.bis.org/basel_framework/standard/MAR.htm

Basel Committee on Banking Supervision (BCBS). (January 2019 (rev. February 2019)). Minimum capital requirments for market risk.

International Swaps Dealers Association (ISDA). (n.d.). ISDA SIMM Methodology: Risk Data Standards.