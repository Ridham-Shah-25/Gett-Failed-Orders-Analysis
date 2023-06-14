## Introduction

Gett, previously known as GetTaxi, is an Israeli-developed technology platform solely focused on corporate Ground Transportation Management (GTM). They have an application where clients can order taxis, and drivers can accept their rides (offers). At the moment, when the client clicks the Order button in the application, the matching system searches for the most relevant drivers and offers them the order. In this task, we would like to investigate some matching metrics for orders that did not completed successfully, i.e., the customer didn't end up getting a car.

## Data Description
We have two data sets: `data_orders` and `data_offers`, both being stored in a CSV format. The `data_orders` data set contains the following columns:

- `order_datetime` - time of the order
- `origin_longitude` - longitude of the order
- `origin_latitude` - latitude of the order
- `m_order_eta` - time before order arrival
- `order_gk` - order number
- `order_status_key` - status, an enumeration consisting of the following mapping:
- `4` - cancelled by client,
- `9` - cancelled by system, i.e., a reject
- `is_driver_assigned_key` - whether a driver has been assigned
- `cancellation_time_in_seconds` - how many seconds passed before cancellation

The `data_offers` data set is a simple map with 2 columns:

- `order_gk` - order number, associated with the same column from the - `orders` data set
- `offer_id` - ID of an offer

## Questions Answered
* Build up distribution of orders according to reasons for failure: cancellations before and after driver assignment, and reasons for order rejection. Analyse the resulting plot. Which category has the highest number of orders?
* Plot the distribution of failed orders by hours. Is there a trend that certain hours have an abnormally high proportion of one category or another? What hours are the biggest fails? How can this be explained?
* Plot the average time to cancellation with and without driver, by the hour. If there are any outliers in the data, it would be better to remove them. Can we draw any conclusions from this plot?
* Plot the distribution of average ETA by hours. How can this plot be explained?
* Using the h3 and folium packages, calculate how many sizes 8 hexes contain 80% of all orders from the original data sets and visualise the hexes, colouring them by the number of fails on the map.

## Conclusion
It is observed that a high number of clients cancelled their order before a driver was assigned, implying that customers probably had waited too long to be assigned a driver and decided on other alternaive transport means.

It is evident that the highest order fails occurred at `8:00`,followed by `21:00` and `23:00`.

The average time to cancellation is higher with an assigned driver than those without assigned driver for each hour without exception.The peak occurred at Hour `5`. At this time there are a lot of client cancellations, so a logical explanation would be that clients have waited too long for the driver.

Order cancellation increases with increasing ETAs, with the highest ETAs happening at 8:00. It is therefore not surprising that the highest order cancellations happen at 8:00 as evident in the count of failed orders per hour.

Highest Number of Order Cancellations are found in and around Reading Town. They need to be investigated further.

Recommendations to reduce cancellations:
- Reduce wait times especially at 7:00 to 8:00 and 16:00 to 17:00 as this time coincides with rush-hour where clients catch a ride to work and from work respectively.
- A reasonable business strategy would be to incentivize people to offer their cars for ride hailing within this time period for higher fares. Thus making more rides available  and thus reducing ETAs.
