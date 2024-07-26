# Privacy vs. Social Capital: Social Media PII Disclosure Analyses

<div align='center'>

[![Kaggle](https://img.shields.io/badge/Kaggle-035a7d?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/code/edyvision/social-media-pii-disclosure-analyses-reddit/)
[![ResearchGate](https://img.shields.io/badge/ResearchGate-00CCBB?style=for-the-badge&logo=ResearchGate&logoColor=white)](https://www.researchgate.net/profile/Eidan-Rosado)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


</div>

This data was used to analyze PII disclosures in threads with special attention to influencer characteristics in the interactions in the dissertation titled `Privacy vs. Social Capital: Examining Information Disclosure Patterns within Social Media Influencer Networks` and the research paper titled `Unveiling Influencer-Driven Personal Data Sharing in Social Media Discourse`.

Author: Eidan Rosado - [@EdyVision](https://github.com/EdyVision)  <br/>
Affiliation: Nova Southeastern University, College of Computing and Engineering

---

## Data Overview
The data is split by the phase in which it was collected. The data in the pilot analysis collection records are limited and were used to test the scripts. The data in the main study collection were used to obtain the insights sought regarding influencer impact on PII disclosures. Social posts in the pilot analysis were collected from Twitter (X) whereas posts from the main study were pulled from Reddit due to a last minute switch in platforms.

<em>
Note: Reddit was selected in the  main study due to unprecedented changes with the Twitter (X) platform in 2023.
</em>

### Analyzed Posts
Each original post is analyzed to annotate the PII tokens disclosed, what trend collection and cluster group the post is associated with, and some insights like hashtags used and time elapsed from the original author's post. These are then eventually summarized in groups in the cluster records.

Included columns and types:

```python
{
    "post_uuid" : str,
    "user_uuid" : str,
    "influence_power" : float,
    "user_follower_count" : int,
    "user_following_count" : int,
    "user_rff_score" : float,
    "user_influencer_tier" : str,
    "post_retweet_count" : int,
    "post_crosspost_count" : int,
    "post_quote_count" : int,
    "post_like_count" : int,
    "post_dislike_count" : int,
    "post_reply_count" : int,
    "post_impression_count" : int,
    "post_engagement_count" : int,
    "mentions" : list,
    "hashtags" : list,
    "url_count" : int,
    "risk_score" : float,
    "pii_detected" : bool,
    "pii_disclosed" : list,
    "string_token_count": int,
    "pii_token_count": int,
    "post_uuids_replied_to" : list,
    "post_uuids_quoted" : list,
    "in_reply_to_user_uuid" : str,
    "is_comment": bool,
    "community": str,  # Excluded in exports due to community guidelines
    "is_text_starter": bool,
    "time_elapsed" : int,
    "collection_name" : str,
    "timestamp" : ISODate,
    "cluster_name" : str
}
```

### Clusters
Each cluster record is a summarization of the analyzed_posts that contain the cluster_name associated with it. Each cluster will have an original conversation starter, and that original conversation starter may or may not be considered an influencer (based on follower count). The original poster, their eigenvector centrality value (saved as influence power), and their influencer tier (Non, Nano, Micro, Mid-Tier, or Macro, Mega) are included with all summaries.

Included columns and types:

```python
{
    "cluster_name" : str,
    "collection_name" : str,
    "graph_details" : {
        "graph" : dict,
        "pos" : dict,
        "node_sizes" : list,
        "node_colors" : list,
        "labels" : dict,
        "title" : str
    },
    "hashtags" : list,
    "influencer_count" : int,
    "influencer_tier_frequencies" : dict,
    "node_count" : int,
    "pii_detection_count" : int,
    "pii_detection_frequencies" : dict,
    "risk_score_max" : float,
    "risk_score_mean" : float,
    "risk_score_median" : float,
    "risk_score_min" : float,
    "timestamp_range" : list,
    "timestamp_span_sec" : float,
    "top_influence_power_score" : float,
    "top_influencer_tier" : str
}
```

