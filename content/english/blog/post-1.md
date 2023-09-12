---
title: "Music and Mental Health: A Statistical Journey"
meta_title: ""
description: "The initial goal was far-reaching but precise: to understand the effectiveness of different music genres on various self-reported mental health conditions. The central research question aimed to answer was, "Do certain genres have a statistically significant positive or negative effect on self-reported stress, anxiety, or depression levels?"
image: /images/sound_healing.jpg
categories: ["Python", "Machine Learning"]
date: 2023-09-08
tags: ["Python", "Tableau"]
draft: false
---
Music is often called the universal language, capable of evoking emotions that words sometimes fail to capture. Yet, can it be more than just a source of entertainment? Can it impact our mental state in a significant way? The primary objective of this project was to explore this fascinating intersection of music and mental health.

#### Project Objective

The initial goal was far-reaching but precise: to understand the effectiveness of different music genres on various self-reported mental health conditions. The central research question aimed to answer was, Do certain genres have a statistically significant positive or negative effect on self-reported stress, anxiety, or depression levels?"

#### Exploratory Data Analysis (EDA): A Prelude to Our Findings

Before diving into the Tableau dashboard, it's essential to note some intriguing trends unearthed during the exploratory data analysis. Rock, Pop, and Metal emerged as intriguing outliers — they were not only popular choices but also genres that showed a higher correlation with depression, anxiety, insomnia, and OCD.

While this was only a snapshot of the comprehensive insights, it highlighted the complexity and duality of the impact that music genres can have on mental health.

<div class='tableauPlaceholder' id='viz1694447228340' style='position: relative; width: 100%;'>
    <noscript>
        <a href='#'><img alt='Dashboard 1 ' src='https://public.tableau.com/static/images/Mx/MxMHDashboard/Dashboard1/1_rss.png' style='border: none' /></a>
    </noscript>
    <object class='tableauViz'  style='display:none; width: 100%; height: 100%;'>
        <param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' />
        <param name='embed_code_version' value='3' />
        <param name='site_root' value='' />
        <param name='name' value='MxMHDashboard&#47;Dashboard1' />
        <param name='tabs' value='no' />
        <param name='toolbar' value='yes' />
        <param name='static_image' value='https://public.tableau.com/static/images/Mx/MxMHDashboard/Dashboard1/1.png' />
        <param name='animate_transition' value='yes' />
        <param name='display_static_image' value='yes' />
        <param name='display_spinner' value='yes' />
        <param name='display_overlay' value='yes' />
        <param name='display_count' value='yes' />
        <param name='language' value='en-US' />
    </object>
</div>
<script type='text/javascript'>
    var divElement = document.getElementById('viz1694447228340');
    var vizElement = divElement.getElementsByTagName('object')[0];
    vizElement.style.width = '100%';
    vizElement.style.height = divElement.offsetWidth * 0.75 + 'px';
    var scriptElement = document.createElement('script');
    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>

#### Project Conclusion

The original hypothesis aimed to test whether music genres have a statistically significant impact on self-reported stress levels. However, as the study progressed, the hypothesis was refined to explore the correlation between the BPM of music genres and self-reported levels of various mental health conditions, such as anxiety.

Through statistical analyses like Pearson correlation and OLS regressions across different age groups, we found nuanced relationships:

- For the age group 18-25, a positive relationship existed between BPM, hours of listening, and anxiety levels.
- In the 26-35 age group, a negative relationship was observed with BPM but a positive relationship with hours of listening.

These findings indicate that the relationship between BPM and mental health conditions is complex and influenced by various factors like age. Although the original hypothesis was not fully validated, the study offers valuable insights for more nuanced future research.

---

Check out my project on [GitHub](https://github.com/MarieM1202/sound_healing).
