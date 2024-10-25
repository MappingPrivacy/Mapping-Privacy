**General overview of the Mapping Privacy dashboard**

This dashboard was created to uncover the real availability of PA API traffic without 3rd-party cookies worldwide and by country. By the courtesy of RTB House, AdLook and PrimeAudience who shared their data with the authors of this report, it has been discovered that the cookieless traffic available via PA API is much lower than the 0.75% claim provided by the Chrome browser and strongly depends on the market and the approach of companies operating in the area.

**All PA API scale**

The straightforward approach of simply comparing the number of PA API bid requests from Chrome browsers without third-party cookies to all incoming bid requests from Chrome is not feasible due to technical differences between PA API and classic bid streams. Such a simplification inflates the numbers leading to false conclusions. The values calculated this way are also visible below the addressable metric to show how much the approach changes the results.

**Addressable PA API scale**

Addressable bid requests are used to present the current scale. These bid requests represent users who are available for a buyer to bid for. Specifically, for this case they are the users who belong to at least one buyer’s interest group. The values are presented in packets aggregated by week. The green or red indicator above the value shows the week-to-week change.

**More technical details**

The addressable PA API scale is calculated with the following formula:

   Scale = a/b * 100%, where:

a — is the number of addressable PA API bid requests from cookieless Chrome

b — is the number of all addressable bid requests from Chrome

The source for counting PA API addressable bid requests is the bid debug reports. Since a single bid request can include multiple interest groups and trigger multiple auctions that result in multiple reports, they are deduplicated by the request ID. Only bid requests from Chrome treatment_1.* labels (cookieless) are included in calculating addressable PA API bid requests. The number of all addressable bid requests from Chrome includes the cookieless PA API, PA API with cookies, and classic bid requests.

This logic is visually presented on the graph in the addressable_paapi_scale.png file.

**Other factors**

Bid debug reports are the main source for the analysis of the incoming bid requests in PA API. Their nature doesn't allow to include certain factors that may influence the results, such as timeouts and bids unanswered for unidentified reasons. Moreover, the buyer not being present on the publisher's buyers list or incomplete PA API campaign migration on the buyer side may also affect the result. There may be other factors influencing the results that could make an argument for inclusion. The different lifetimes of cookies and interest groups also influence the results, but these disparities come from the native attributes of those two environments. It was a conscious decision not to include this specific factor in the calculations.

Since bid debug reports are the sole source for analyzing incoming bid requests in PA API, it is important to note that Chrome plans to throttle them in the future. Once that happens, the calculations will no longer be feasible. While some estimations might still be possible if the sampling size is known, the overall accuracy will decrease.

