AI Writing & Analytics – Workflow Memo
Purpose & Scope
This memorandum details how generative-AI tools were orchestrated to produce the Customer Behavior Analysis and Retention Strategy, in compliance with our course requirement for full methodological transparency. The final deliverable included:
•	a data-driven segmentation of the customer base with key behavioral traits identified,
•	a predictive model for 90-day repeats purchase propensity with feature importance analysis,
•	cohort-based retention and customer lifetime value (CLV) projections,
•	actionable recommendations for improving retention and monetization of each segment,
•	a minimum of ten APA-formatted citations from peer-reviewed marketing analytics sources.
The memo explains the AI toolchain, prompt engineering techniques, human oversight, and quality controls that accelerated data analysis and report drafting while safeguarding academic integrity.
AI Toolchain & Prompt Strategy
Tool	Role in Workflow	Representative Prompt/Script
Gemini Pro	Multi-pass research assistant and narrative drafter	“Summarize key factors influencing customer churn from the attached journal PDF.”
OpenAI Retrieval Agent	Vector-indexed memory to keep key metrics, definitions, and cited facts consistent across sections	“Retrieve the average 6-month retention rate we used in Draft 2.”
Perplexity AI (Web)	Source-backed web research for live industry benchmarks and academic insights on customer retention	“Latest annual churn rate in e-commerce sector (with APA citation).”
Python (pandas, numpy)	Single source of truth for all data calculations; automated CLV computation, retention cohort analysis, and significance testing	clv = transactions.groupby('customer_id').agg(total_value=('amount', 'sum'))
scikit-learn	Predictive modeling (random forest classifier) to identify drivers of repeat purchase; ROC analysis and feature importance extraction	clf = RandomForestClassifier(n_estimators=100).fit(X_train, y_train)
Matplotlib + Seaborn	Auto-generated retention curves, CLV distributions, and feature importance plots in the report’s style palette	sns.barplot(x=features, y=importances)
Grammarly + Microsoft Editor	Final grammar, style, and third-person voice assurance	(Post-export editing pass with formal style guide applied)
Prompt Engineering Highlights
•	Clarity & Specificity: Prompts were kept short, explicit, and outcome-oriented (e.g., “List five notable patterns from the customer segmentation analysis”).
•	Iterative Refinement: A living prompt log captured each query and generation iteration, enabling rapid rollback or adjustment if a modification reduced clarity or accuracy.
•	Rubric-Guided Retrieval: Retrieval-agent prompts followed a checklist derived from the assignment rubric to confirm every required element (e.g., all segments described, each recommendation supported by data) was addressed before submission.
Gemini / LLM prompt log 
Prompt	Purpose
“Summarise the top three retention risks from this cohort heat map JSON…”	Executive summary drafting
“Generate five loyalty campaign ideas for high CLV copier buyers.”	Strategy ideation
“Explain the difference between frequency and monetary in RFM in plain English (≤60 words).”	Report clarity
“Suggest a Looker Studio dashboard layout for CLV and retention metrics.”	Dashboard planning
“Create a SQL query to compute rolling 90 day repurchase rate in BigQuery.”	Coding assist

End-to-End Workflow
1.	Data Ingestion — Historical sales and customer interaction data were loaded into the analysis environment, and key documents (prior reports, relevant research papers) were embedded in a retrieval layer for context. Perplexity AI supplemented internal data with up-to-date industry benchmarks (e.g., average e-commerce retention rates and CLV figures) to ground the analysis in external context.
2.	Exploratory Analysis — Gemini was used in an initial pass to outline potential customer segments and hypotheses based on RFM (Recency, Frequency, Monetary value) patterns. Python (pandas) scripts then executed the heavy lifting: cleaning data, computing RFM scores, performing a chi-square analysis to validate segment differences, and surfacing preliminary insights. Gemini subsequently reviewed these findings, suggesting interpretations (for example, noting if one segment showed significantly higher affinity for certain product categories) to guide deeper exploration.
3.	Modeling & Insights — Using scikit-learn, a 90-day repeat purchase propensity model was trained, and an ROC curve was generated to evaluate its performance. GPT-o3 analyzed the model output, translating feature importance scores into plain-language insights (e.g., highlighting that recency of last purchase was the strongest predictor of repeat behavior). The AI also cross-checked model results against initial hypotheses, ensuring consistency between the statistical analysis and the emerging narrative.
4.	Documentation & Citation — Claude’s “APA assistant” mode helped draft the report’s text, weaving in findings with proper in-text citations. It automatically formatted references for any external metrics or best practices mentioned (for instance, citing a Harvard Business Review study on customer retention drivers). Meanwhile, the retrieval agent flagged any uncited assertions in the draft, prompting the team to provide sources or evidence for each claim before finalizing the document.
5.	Visual Creation — Python’s Matplotlib and Seaborn libraries rendered key visuals such as cohort retention curves, CLV distribution histograms, and feature importance bar charts. Feature importance chart showing key drivers of 90-day purchase propensity. GPT-4 integrated these visuals into the narrative by generating figure descriptions and ensuring each graphic was introduced with proper context in the text. Tables (e.g., segment summary statistics) were generated in Markdown for seamless conversion to Word, allowing one-click inclusion of data tables in the final report.
6.	Iterative Refinement — The draft underwent three full revision cycles, incorporating human feedback on clarity, tone, and alignment with assignment requirements. This AI-augmented process was completed in roughly half the iterations normally needed; by comparison, similar projects previously required six or more rounds of manual drafting to reach the same quality standard.
7.	Final Polishing — Grammarly and Microsoft Editor were employed in the final pass to enforce a formal third-person tone, eliminate any colloquialisms, and correct grammatical inconsistencies. The finished strategy memo was then reviewed by a peer for quality assurance before submission.
Human Oversight Touchpoints
•	Domain Expert Review — Marketing analytics and data science experts reviewed the segment definitions, statistical methods, and modeling approach to ensure the AI’s outputs were grounded in sound methodology and industry knowledge.
•	Statistical Verification — A human analyst cross-verified critical figures (such as retention rates and model accuracy) and reran key analyses on a sample basis to ensure the AI’s results were reproducible and free of errors or misinterpretation.
•	Tone & Bias Control — Editors moderated the report’s language, ensuring an objective, academic tone with no exaggerated claims. They also checked that the AI hadn’t introduced any unintended bias, especially in how customer segments were described or how recommendations were framed.
•	Approval Gate — Each section of the deliverable passed an approval checkpoint requiring two human sign-offs (e.g., one from a content expert and one from a project lead) confirming factual accuracy, proper citation, and logical flow. No AI-generated content was accepted until it cleared this dual sign-off process.
Ethical & Quality Safeguards
•	Citation Integrity — Every statistic, quote, or external fact in the report was traced to a credible source. Automated checks verified that each in-text citation had a corresponding entry in the reference list and that all URLs/DOIs were accessible. Any broken or questionable sources were promptly replaced or removed.
•	Hallucination Defense — No AI-generated insights or data were taken at face value without validation. If GPT-4 provided a figure or trend, the team corroborated it against the actual dataset or a trusted external source before inclusion. This two-step verification prevented fabricated information from seeping into the analysis.
•	Consistency Checker — A custom Python/LangChain routine scanned the draft for internal consistency, flagging any contradictory numbers or segment labels (for instance, if one section mentioned 5 segments while another mentioned 6). This ensured the narrative, data tables, and visuals all told a coherent, unified story.
•	Accessibility Compliance — The report was structured with logical headings and alt-text for all visuals to meet inclusive design standards. Color choices in charts followed accessibility guidelines for contrast. We verified that the final document was screen-reader friendly, reflecting a commitment to universal readability.
•	Privacy Controls — All customer data used were anonymized and handled in compliance with data privacy regulations. No sensitive personal identifiers were ever uploaded to AI tools. The AI systems operated within a secure sandbox, and all analyses adhered to the institution’s data usage policies, ensuring that augmenting our workflow with AI did not compromise client or customer confidentiality.
Future Enhancements
1.	Automated Diagramming — Utilize tools like Mermaid or D2 to auto-generate diagrammatic workflows (e.g., customer journey maps or segment decision trees) directly from text prompts, reducing the need for manual visualization work.
2.	Live Data Integration — Connect the analysis pipeline to live data sources (such as the company’s data warehouse or CRM via API) for real-time updates to retention metrics and segment performance, ensuring the strategy remains up-to-date post-delivery.
3.	Citation Gap Detector — Deploy a background AI agent that continuously scans drafts for uncited statements and suggests potential references from a curated database of marketing journals and industry reports, further safeguarding against accidental plagiarism or unsupported claims.
4.	Domain-Specific Model Tuning — Fine-tune language models on retail and customer analytics corpora, as well as on prior approved reports, to better align AI-generated content with domain terminology and the expected analytical depth, minimizing the need for post-edit revisions.
5.	Unified Agent Pipeline — Experiment with an orchestrated multi-agent workflow (e.g., using an OpenAI Functions chain or a LangChain pipeline) that seamlessly links data retrieval, statistical analysis, visualization, and narrative drafting. This would allow future projects to execute a major part of the report generation through a single, cohesive AI-driven process, supervised by human checkpoints.

