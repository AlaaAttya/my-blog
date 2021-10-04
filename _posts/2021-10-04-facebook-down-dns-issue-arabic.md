---
id: 131
title: الحق فيسبوك واقع
date: 2015-01-15T23:45:04+00:00
author: alaa
layout: article
tags:
    - dns
    - facebook-down
    - BGP
    - networking
    - BGP-peering
    - arabic-blogs
key: facebook-down-dns-issue-arabic-131
lang: ar
---
**بدايه انا مش متخصص في مجال ال networking و الكلام اللي هنا دا علي حسب فهمي و علي حسب ما دورت**

لو في اي معلومه مش مظبوطه او مش دقيقه ممكن ت create pull request and contribute here <3 [https://github.com/AlaaAttya/my-blog](https://github.com/AlaaAttya/my-blog)

خلينا نتكلم كلام technical شويه عن مشكله facebook و ازاي حصلت

خلينا الاول نتكلم بمثال يقرب الموضوع: تخيل انك عايز تبعت جواب من برلين في المانيا ل الاسكندريه في مصر.
عشان نعمل كدا بترمي الجواب في صندوق البوسطه. و بعدين بيروح الجواب لمكتب البريد التابع للمنطقه اللي انت ساكن فيها. مكتب البريد دا عنده زي جدول فيه كل الطرق الممكنه عشان يوصل الجواب مابين برلين لالمانيا. طيب علي اي اساس هيقرر انه يختار الطريق. يبقي علي حسب قواعد هوا حاططها. يعني مثلا لو بريد سريع هيختار اسرع طريق. لو بريد بتكلفه شحن قليله هيختار الطرق اللي متكلفهوش كتير.

مثلا الجواب دا هيتنقل ما بين مكاتب بريد الاول جوا المانيا و دا بنقول عليه internal routing يعني مثلا يطلع من مكتب بريد حي charlottenburg في برلين ل مكتب بريد حي Mitte في برلين و بعدين مكتب بريد تاني في مدينه تانيه مثلا ميونخ (كل دا احنا لسه جوا المانيا ف دا اسمه internal routing) و كل مكتب بريد عنده routing table بيقوله مين اقرب و احسن مكتب ممكن يروحله
بعدها عايزين نعرف مين اقرب دوله لمصر عشان نديها الجواب دا ودا اللي بنقول عليه external routing
و لما يوصل مصر هيحصله برضه internal routing لحد ما يوصل للي هيستلم الجواب في اسكندريه.

الخلاصه من الموضوع ان كل مكتب بيبقي عنده routing table و بناء علي شويه rules بيعرف مين المكتب اللي جاي.

خلينا نعمل اسقاطات technical شويه بناء علي القصه اللي فاتت
خلينا نقول علي مجموعه مكاتب بريد المانيا انها بتسمي autonomous system. نفس الكلام بيسمي علي مجموعه مكاتب بريد مصر.
مجموعه مكاتب المانيا تعرف توصل الجوابات جوا المانيا بس متعرفش جوابات جوا مصر. ف هيا عندها routing table بيقولها ان النمسا ممكن توصل الجوابات لمصر و اليونان تعرف توصل الجوابات لمصر و تركيا تعرف برضه توصل لمصر. طيب المانيا هتختار انهو طريق فيهم؟ هتختار عن طريق algorithm
اسمه BGP او ما يسمي بال Boarder Gateway Protocol و هوا المسؤال انه يختار احسن route بناء علي شويه configuration موجوده في كل محطه و  ف للتبسيط هنقول ان AS1 عايزه تكلم AS2. عشان تعمل كدا دا بيسمي BGP peering.
كل AS بيبقي عندها routes ل range معين من ال IPs بيقولو عليها "IP address space."

عشان كل autonomous system يوصل لل autonomous system اللي بعده بيعمل حاجه اسمها BGP peering

خلينا بقي نعمل اسقاط للكلام دا علي الانترنت. تخيل انك بتفتح موقع اسمه hamada.com و انت في برلين و السيرفرات بتاعه الموقع دا في مصر. ازاي دا هيحصل؟

انت مثلا في برلين موصل نت من فودافون. ال request بتاعك هيروح علي vodafone و هيا هتشوف هل هيا عندها اي server بال IP دا؟ الاجابه هتكوت لا. هتروح تسال ال BGP مين احسن route؟ هيقولها دا في شركه اسمها حماده انترنت مثلا هيا دي احسن route. عشان يسال حماده نت عن ال routing table بتاعها و يعمل exchange لل data دي هيعمل حاجه اسمها BGP peering و اي config غلط مش هيعرف يوصل ل حماده نت دي او مثلا تخيل ان حماده نت بعتته ل شركه مثلا اسمها ام احمد نت و ام احمد نت دي اصلا متعرفش اي حاجه عن ال IP اللي انت عايز تروحله. او حتي متعرفش مين من ال autonomous systems عنده ال routes بتاعته. كدا ال request بتاعك عمره ما هيوصل بسبب ان   حماده نت بعتك ل route غلط و كمان قال لكل ال autonomous systems ان اي حد في range ال IPs دا وديه علي "ام احمد نت"

تكمله لموضوع ال BGP routes ال BGP routes دي ممكن تكون internal BGP routes او external BGP routes

في المثال اللي فات كنا بنتلكم علي external BGP routes ال internal BGP routes بتبقي جوا ال  autonomous system نفسه. لانه مثلا حد زي google او facebook عنده data centres كتير هوا خلاص ال request وصل لل DNS بتاع facebook بس مش عارف ال data centre اللي موجود فيه ال machine اللي ال IP بتاعها كذا.  ف بيبقي في routers كل router بيبقي عنده routing table بيقوله لو ال machine دي عنده ولا يروح ل router تاني. اي config غلط في اي router من دول هيادي ان ال request مش عارف يروح فين او ان router منهم يبعتك ل router غلط بسبب ان ال routes table اصلا غلط و هوا نفسه عمل publish لل routes دي لكذا router تاني و كدا routers كتير اتلطت بسبب config في router غلط. او مثلا  واحد من ال routers دول بقي unavailable معني كدا ان ال route القديم دا مبقاش ينفع نستخدمه تاني و محتاجين نعمل update لل routing tables من تاني و محصلش update لسبب ما. ف برضه ال request مش عارف يوصل

لو حصل اي misconfiguration ممكن يحصل مشكلتين. ان ال routing table اللي موجود في كل router يكون فيه invalid routes و ممكن اصلا ال routes مش عارفين يعملو communicate او exchange information مع بعض بسبب شويه invalid BGP roles
الاسواء بقي ان كل BGP تبدا تعمل exchange ل invalid routes و بكدا كل ال routing tables تبقي corrupted

دي رسمه ممكن توضح الموضوع شويه
<img class="image image--xl" style="width: 100%" src="/assets/images/as-diagram.png"/>

ودا ازاي بيحصل ال BGP peering ما بين ال ISPs

<img class="image image--xl" style="width: 100%" src="/assets/images/isp-peering.gif"/>

طيب ليه الموضوع واخد وقت كتير. لان محدش عارف مين من ال routers عنده bad config و كمان حد كان كاتب ان عشان تعمل reconfigure ل router انت محتاج physical access عشان تعرف توصله و بسبب ال pandemic و كرونا مش كل الناس شغاله onsite في ناس كتير شغاله remote ف الموضوع واخد وقت

في قصه ظريفه حصلت في 2004 ان في شركه ISP (خلينا نقول انها حاجه زي WE او فودافون او غيرهم يعني) عملت publish ل BGP routes غلط و routes دي كان مكتوب فيها انها اسرع routes لاي entities علي ال internet. وبدا كل entity تعمل exchange لنفس ال bad BGP routes و بقت ال bad routes دي سبب في ان مواقع كتير كانت unreachable

في حادثه تانيه برضه ان في ٢٠١٨ في attacker عملو publish ل BGP routes تخلي اي حد بيحاول يوصل ل amazon انه يروح لل servers بتاعه ال attackers دول و سرقو $100,000 


شويه مصادر قريتها عشان اجمع الكلام دا:
- [https://www.juniper.net/documentation/us/en/software/junos/bgp/topics/topic-map/autonomous-systems.html](https://www.juniper.net/documentation/us/en/software/junos/bgp/topics/topic-map/autonomous-systems.html)
- [https://www.cloudflare.com/learning/network-layer/what-is-an-autonomous-system/](https://www.cloudflare.com/learning/network-layer/what-is-an-autonomous-system/)
- [https://www.juniper.net/documentation/us/en/software/junos/bgp/topics/topic-map/bgp-peering-sessions.html](https://www.juniper.net/documentation/us/en/software/junos/bgp/topics/topic-map/bgp-peering-sessions.html) 
- [https://www.cloudflare.com/learning/security/glossary/what-is-bgp/](https://www.cloudflare.com/learning/security/glossary/what-is-bgp/)
