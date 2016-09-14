---
layout: documentation
id: com1
categories:
- documentation
- commerce
title: Commerce API 1.0
excerpt: Use the Ticketmaster Commerce API to look up available offers and products on various platforms, including Ticketmaster's and TicketWeb's. Once offers and products are selected, you can use the API to cart and transact on those items.
keywords: API, commerce API, reserve tickets, retrieve barcode
---

# Commerce API
{: .article}
Use the Ticketmaster Commerce API to look up available offers and products on various platforms, including Ticketmaster's and TicketWeb's. Once offers and products are selected, you can use the API to cart and transact on those items.
{: .article .lead}

#### Developer Console
{: .aside .gray}

Test this endpoint right now in the interactive docs:

[INTERACTIVE DOCS](/products-and-docs/apis/interactive-console/){: .button}

## Event Offers
{: .article .console-link #event-offers}

**Method:** GET.
Authentication required.

Returns Event Offers.

commerce/{version}/events/{id}/offers.{format}
{: .code .red}

### URL parameters:

| Parameter  | Description          | Type              | Default Value      | Required |
|:-----------|:---------------------|:----------------- |:------------------ |:-------- |
| `version`  | The API Version.     | string            |       "v2"         | Yes      |
| `id`       | Event ID. Required.  | string            | "05004F24E0B864B3" | Yes      |
| `format`   | API Response Format. | string            |       "json"       | Yes      |

### Response structure:

{: .nested-list}
- `limits` (object) - limits for event.
    * `max` (object) - max limit.
- `prices` (object) - set of distinct sellable prices for the event.
    * `data` (array) - container for prices data.
        + `{array item object}` - price.
            - `type` (string) - type of price.
            - `attributes` (object) - attributes of price.
                * `currency` (string) - currency of price.
                * `value` (string) - the offered price.
            - `relationships` (object) - available relationships.
                * `offers` (object) - offers that are sellable at this price.
                    - `data` (array) - container for offers.
                        + `{array item object}` - offer.
                            * `id` (string) - id of offer.
                            * `type` (string) - type of offer.
                * `price-zones` (object) - price-zones that are sellable at this price.
                    - `data` (array) - container for price zones.
                        + `{array item object}` - price zone.
                            * `id` (string) - id of price zone.
                            * `type` (string) - type of price zone.                 
- `offers` (array) - container for the set of sellable offers.
    + `{array item object}` - offer.
        * `id` (string) - id.
        * `type` (string) - type.
        * `attributes` (object) - attributes of offer.
            - `name` (string) - name.
            - `description` (string) - description.
            - `rank` (number) - rank.
            - `currency` (string) - currency.            
            - `prices` (array) - prices.
                + `{array item object}` - price.
                    * `value` (string) - price value.        
                    * `total` (string) - total price.         
                    * `fees` (array) - fees.
                        + `{array item object}` - fee.
                            - `value` (string) - fee value.
                            - `label` (string) - fee label.
                            - `type` (string) - fee type.
                    * `taxes` (array) - taxes.
                        + `{array item object}` - tax.
                            - `value` (string) - tax value.
                            - `label` (string) - tax label.
                            - `type` (string) - tax type.
                    * `price-zone` (string) - price zone.                    
            - `limit` (object) - limit.
                - `min` (number) - min.
                - `max` (number) - max.
                - `multiplies` (number) - multiplies.
            - `offer-type` (string) - offer type.       
        * `relationships` (object) - available relationships.
            * `areas` (object) - related areas.
                - `data` (array) - container for areas.
                    + `{array item object}` - area.
                        * `id` (string) - id of area.
                        * `type` (string) - type of area.            
            * `products` (object) - related products.
                * `data` (array) - container for products.
                    + `{array item object}` - product.
                        - `id` (string) - id of product.
                        - `type` (string) - type of product.
            * `price-zones` (object) - related price zones.
                * `data` (array) - container for price zones.
                    + `{array item object}` - price zone.
                        - `id` (string) - id of price zone.
                        - `type` (string) - type of price zone.
- `_embedded` (object) - container for included (embedded) data.
    - `areas` (object) - event areas.
        - `data` (array) - container for areas.
            + `{array item object}` - area.
                * `id` (string) - id of area.
                * `type` (string) - type of area.
                * `attributes` (object) - attributes of areas.
                    - `rank` (string) - rank of area.
                    - `name` (string) - name of area.
                    - `area-type` (string) - type of area.
                * `relationships` (object) - available relationships.
                    - `areas` (object) - related areas.
                        * `data` (array) - areas.
                            + `{array item object}` - container for areas.
                                - `id` (string) - id of area.
                                - `type` (string) - type of area.
                    - `offers` (object) - related offers.
                        * `data` (array) - container for offers.
                            + `{array item object}` - offer.
                                - `id` (string) - id of offer.
                                - `type` (string) - type of offer.
                    - `price-zones` (object) - related price zones.
                        * `data` (array) - container for price zones.
                            + `{array item object}` - price zone.
                                - `id` (string) - id of price zone.
                                - `type` (string) - type of price zone.
    - `passwords` (object) - passwords.
        - `data` (array) - container for passwords.
            + `{array item object}` - password.
                * `id` (string) - password id.
                * `type` (string) - password type.
                * `attributes` (object) - attributes of passwords.
                - `name` (string) - name.
                - `exclusive` (boolean) - is exclusive.
                - `prompts` (array) - prompts.
                    + `{array item object}` - prompt.
                    * `text` (string) - text of prompt.
                - `text-label` (string) - text label.
                * `relationships` (object) - available relationships.
                - `offers` (object) - related offers.
                    * `data` (array) - container for offers.
                    + `{array item object}` - offer.
                        - `id` (string) - id of offer.
                        - `type` (string) - type of offer.
    - `price-zones` (object) - price zones.
        - `data` (array) - container for price zones.
            + `{array item object}` - price zone.
                * `id` (string) - price zone id.
                * `type` (string) - price zone type.
                * `attributes` (object) - attributes of price zone.
                    - `currency` (string) - currency of price zone.
                    - `name` (string) - name of price zone.
                * `relationships` (object) - available relationships.
                    - `offers` (object) - related offers.
                        * `data` (array) - container for offers.
                            + `{array item object}` - offer.
                                - `id` (string) - id of offer.
                                - `type` (string) - type of offer.
                    - `areas` (object) - related areas.
                        - `data` (array) - container for areas.
                            + `{array item object}` - area.
                                * `id` (string) - id of area.
                                * `type` (string) - type of area.

{: .aside}
>[JS](#js)
>[cURL](#curl)
{: .lang-selector}

{% highlight js %}
$.ajax({
  type:"GET",
  url:"https://app.ticketmaster.com/commerce/v2/events/0B00508C829A3875/offers.json?{apikey}",
  async:true,
  dataType: "json",
  success: function(json) {
              console.log(json);
              // Parse the response.
              // Do other things.
           },
  error: function(xhr, status, err) {
              // This time, we do not end up here!
           }
});
{% endhighlight %}

{% highlight bash %}
curl \
--include 'https://app.ticketmaster.com/commerce/v2/events/0B00508C829A3875/offers.json?{apikey}
{% endhighlight %}


{: .article}
>[Request](#req)
>[Response](#res)
{: .reqres}

{% highlight HTTP %}
GET /commerce/v2/events/0B00508C829A3875/offers.json?{apikey} HTTP/1.1
Host: app.ticketmaster.com
X-Target-URI: https://app.ticketmaster.com
Connection: Keep-Alive
{% endhighlight %}

{% highlight HTTP %}
HTTP/1.1 200 OK
Rate-Limit-Over:
0
Content-Length:
21532
Rate-Limit-Available:
498399
Set-Cookie:
CMPS=EB55hDR95pURN1HyCaJoxuyEQcA8Sv2aKm4J/YaMBOYTHywQO/XHcWL6t8TWHLkL; path=/
Access-Control-Allow-Methods:
POST, PATCH, DELETE, GET, HEAD, OPTIONS
X-TM-SESSION-BID:
commerce-offering
Connection:
keep-alive
Access-Control-Allow-Credentials:
true
Server:
Apache-Coyote/1.1
Rate-Limit-Reset:
1468530242515
Access-Control-Allow-Headers:
Origin, Accept, X-Requested-With, Content-Type, Access-Control-Request-Method, Access-Control-Request-Headers
Date:
Thu, 14 Jul 2016 18:15:12 GMT
Access-Control-Allow-Origin:
*
X-TM-SESSION-SID:
49D8E7AAEF70BE318E4CEB599C499675
X-Application-Context:
commerce-api-commerce-offering-v1:default,jash1:8080
Content-Type:
application/json;charset=UTF-8
Rate-Limit:
500000

{
  "limits":  {
    "max": 50
  },
  "prices":  {
    "data":  [
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "14.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "000000000001",
                "type": "offers"
              },
               {
                "id": "QMASK2ROLLUP",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "23",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "7",
                "type": "areas"
              },
               {
                "id": "22",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "18.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "000000000001",
                "type": "offers"
              },
               {
                "id": "QMASK2ROLLUP",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "20",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "7",
                "type": "areas"
              },
               {
                "id": "22",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "23.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "QMASK2ROLLUP",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "19",
                "type": "price-zones"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "25.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "000000000001",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "19",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "6",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "26.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "QMASK2ROLLUP",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "17",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "6",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "28.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "QMASK2ROLLUP",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "15",
                "type": "price-zones"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "30.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "000000000001",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "17",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "6",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "36.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "000000000001",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "15",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "5",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "37.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "QMASK2ROLLUP",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "13",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "5",
                "type": "areas"
              },
               {
                "id": "22",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "44.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "QMASK2ROLLUP",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "12",
                "type": "price-zones"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "59.00"
        },
        "relationships":  {
          "priceZones":  {
            "data":  [
               {
                "id": "11",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "22",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "66.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "QMASK2ROLLUP",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "11",
                "type": "price-zones"
              },
               {
                "id": "12",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "22",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "70.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "000000000001",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "13",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "5",
                "type": "areas"
              },
               {
                "id": "22",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "85.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "000000000001",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "12",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "4",
                "type": "areas"
              },
               {
                "id": "8",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "100.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "000000000001",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "11",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "4",
                "type": "areas"
              },
               {
                "id": "14",
                "type": "areas"
              },
               {
                "id": "22",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "125.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "QMASK2ROLLUP",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "10",
                "type": "price-zones"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "142.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "QMASK2ROLLUP",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "9",
                "type": "price-zones"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "150.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "000000000001",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "10",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "2",
                "type": "areas"
              },
               {
                "id": "3",
                "type": "areas"
              }
            ]
          }
        }
      },
       {
        "type": "offered-prices",
        "attributes":  {
          "currency": "USD",
          "value": "182.00"
        },
        "relationships":  {
          "offers":  {
            "data":  [
               {
                "id": "000000000001",
                "type": "offers"
              }
            ]
          },
          "priceZones":  {
            "data":  [
               {
                "id": "9",
                "type": "price-zones"
              }
            ]
          },
          "areas":  {
            "data":  [
               {
                "id": "0",
                "type": "areas"
              },
               {
                "id": "1",
                "type": "areas"
              }
            ]
          }
        }
      }
    ]
  },
  "metadata":  {
    "eventMapping":  {
      "id": "vvG1iZfFweJN-g",
      "type": "event",
      "source":  {
        "name": "ticketmaster",
        "id": "0B00508C829A3875"
      }
    }
  },
  "offers":  [
     {
      "id": "000000000001",
      "type": "offers",
      "attributes":  {
        "name": "ADULT",
        "description": "Standard Adult",
        "rank": 0,
        "offerType": "DEFAULT",
        "currency": "USD",
        "prices":  [
           {
            "priceZone": "10",
            "value": "150.00",
            "total": "165.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "15.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "11",
            "value": "100.00",
            "total": "111.00",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "11.00",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "12",
            "value": "85.00",
            "total": "94.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "9.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "13",
            "value": "70.00",
            "total": "79.00",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "9.00",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "15",
            "value": "36.00",
            "total": "43.00",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "7.00",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "17",
            "value": "30.00",
            "total": "37.00",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "7.00",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "19",
            "value": "25.00",
            "total": "31.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "6.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "20",
            "value": "18.00",
            "total": "23.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "5.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "23",
            "value": "14.00",
            "total": "19.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "5.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "9",
            "value": "182.00",
            "total": "199.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "17.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          }
        ],
        "limit":  {
          "min": 1,
          "max": 50,
          "multiples": 1
        }
      },
      "relationships":  {
        "areas":  {
          "data":  [
             {
              "id": "0",
              "type": "areas"
            },
             {
              "id": "1",
              "type": "areas"
            },
             {
              "id": "2",
              "type": "areas"
            },
             {
              "id": "3",
              "type": "areas"
            },
             {
              "id": "4",
              "type": "areas"
            },
             {
              "id": "5",
              "type": "areas"
            },
             {
              "id": "6",
              "type": "areas"
            },
             {
              "id": "7",
              "type": "areas"
            },
             {
              "id": "8",
              "type": "areas"
            },
             {
              "id": "14",
              "type": "areas"
            },
             {
              "id": "22",
              "type": "areas"
            }
          ]
        },
        "priceZones":  {
          "data":  [
             {
              "id": "10",
              "type": "price-zones"
            },
             {
              "id": "11",
              "type": "price-zones"
            },
             {
              "id": "12",
              "type": "price-zones"
            },
             {
              "id": "13",
              "type": "price-zones"
            },
             {
              "id": "15",
              "type": "price-zones"
            },
             {
              "id": "17",
              "type": "price-zones"
            },
             {
              "id": "19",
              "type": "price-zones"
            },
             {
              "id": "20",
              "type": "price-zones"
            },
             {
              "id": "23",
              "type": "price-zones"
            },
             {
              "id": "9",
              "type": "price-zones"
            }
          ]
        },
        "products":  {
          "data":  [
             {
              "id": "0B00508C829A3875",
              "type": "products"
            }
          ]
        }
      }
    },
     {
      "id": "QMASK2ROLLUP",
      "type": "offers",
      "attributes":  {
        "name": "QMASK2ROLLUP",
        "rank": 1,
        "offerType": "SPECIAL",
        "currency": "USD",
        "prices":  [
           {
            "priceZone": "10",
            "value": "125.00",
            "total": "137.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "12.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "11",
            "value": "66.00",
            "total": "74.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "8.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "12",
            "value": "44.00",
            "total": "51.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "7.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "13",
            "value": "37.00",
            "total": "44.00",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "7.00",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "15",
            "value": "28.00",
            "total": "34.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "6.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "17",
            "value": "26.00",
            "total": "32.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "6.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "19",
            "value": "23.00",
            "total": "29.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "6.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "20",
            "value": "18.00",
            "total": "23.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "5.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "23",
            "value": "14.00",
            "total": "19.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "5.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          },
           {
            "priceZone": "9",
            "value": "142.00",
            "total": "156.50",
            "fees":  [
               {
                "value": "0.00",
                "label": "Distance",
                "type": "distance"
              },
               {
                "value": "0.00",
                "label": "Facility",
                "type": "facility"
              },
               {
                "value": "14.50",
                "label": "Service",
                "type": "service"
              }
            ],
            "taxes":  [
               {
                "value": "0.00",
                "label": "Face Value Tax",
                "type": "face_value_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax",
                "type": "service_tax"
              },
               {
                "value": "0.00",
                "label": "Service Tax 2",
                "type": "service_tax2"
              }
            ]
          }
        ],
        "limit":  {
          "min": 1,
          "max": 50,
          "multiples": 1
        }
      },
      "relationships":  {
        "areas":  {
          "data":  [
             {
              "id": "0",
              "type": "areas"
            },
             {
              "id": "1",
              "type": "areas"
            },
             {
              "id": "2",
              "type": "areas"
            },
             {
              "id": "3",
              "type": "areas"
            },
             {
              "id": "4",
              "type": "areas"
            },
             {
              "id": "5",
              "type": "areas"
            },
             {
              "id": "6",
              "type": "areas"
            },
             {
              "id": "7",
              "type": "areas"
            },
             {
              "id": "8",
              "type": "areas"
            },
             {
              "id": "14",
              "type": "areas"
            },
             {
              "id": "22",
              "type": "areas"
            }
          ]
        },
        "priceZones":  {
          "data":  [
             {
              "id": "10",
              "type": "price-zones"
            },
             {
              "id": "11",
              "type": "price-zones"
            },
             {
              "id": "12",
              "type": "price-zones"
            },
             {
              "id": "13",
              "type": "price-zones"
            },
             {
              "id": "15",
              "type": "price-zones"
            },
             {
              "id": "17",
              "type": "price-zones"
            },
             {
              "id": "19",
              "type": "price-zones"
            },
             {
              "id": "20",
              "type": "price-zones"
            },
             {
              "id": "23",
              "type": "price-zones"
            },
             {
              "id": "9",
              "type": "price-zones"
            }
          ]
        },
        "passwords":  {
          "data":  [
             {
              "id": "2b81df841235ca20f272acad674d6c71",
              "type": "passwords"
            }
          ]
        },
        "products":  {
          "data":  [
             {
              "id": "0B00508C829A3875",
              "type": "products"
            }
          ]
        }
      }
    }
  ],
  "_embedded":  {
    "priceZones":  {
      "data":  [
         {
          "id": "17",
          "type": "price-zones",
          "attributes":  {
            "currency": "USD",
            "name": "PRICE LEVEL 7"
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "areas":  {
              "data":  [
                 {
                  "id": "6",
                  "type": "areas"
                }
              ]
            }
          }
        },
         {
          "id": "20",
          "type": "price-zones",
          "attributes":  {
            "currency": "USD",
            "name": "PRICE LEVEL 9"
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "areas":  {
              "data":  [
                 {
                  "id": "7",
                  "type": "areas"
                },
                 {
                  "id": "22",
                  "type": "areas"
                }
              ]
            }
          }
        },
         {
          "id": "10",
          "type": "price-zones",
          "attributes":  {
            "currency": "USD",
            "name": "PRICE LEVEL 2"
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "areas":  {
              "data":  [
                 {
                  "id": "2",
                  "type": "areas"
                },
                 {
                  "id": "3",
                  "type": "areas"
                }
              ]
            }
          }
        },
         {
          "id": "11",
          "type": "price-zones",
          "attributes":  {
            "currency": "USD",
            "name": "PRICE LEVEL 3"
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "areas":  {
              "data":  [
                 {
                  "id": "4",
                  "type": "areas"
                },
                 {
                  "id": "14",
                  "type": "areas"
                },
                 {
                  "id": "22",
                  "type": "areas"
                }
              ]
            }
          }
        },
         {
          "id": "23",
          "type": "price-zones",
          "attributes":  {
            "currency": "USD",
            "name": "PRICE LEVEL 10"
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "areas":  {
              "data":  [
                 {
                  "id": "7",
                  "type": "areas"
                },
                 {
                  "id": "22",
                  "type": "areas"
                }
              ]
            }
          }
        },
         {
          "id": "13",
          "type": "price-zones",
          "attributes":  {
            "currency": "USD",
            "name": "PRICE LEVEL 5"
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "areas":  {
              "data":  [
                 {
                  "id": "5",
                  "type": "areas"
                },
                 {
                  "id": "22",
                  "type": "areas"
                }
              ]
            }
          }
        },
         {
          "id": "9",
          "type": "price-zones",
          "attributes":  {
            "currency": "USD",
            "name": "PRICE LEVEL 1"
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "areas":  {
              "data":  [
                 {
                  "id": "0",
                  "type": "areas"
                },
                 {
                  "id": "1",
                  "type": "areas"
                }
              ]
            }
          }
        },
         {
          "id": "12",
          "type": "price-zones",
          "attributes":  {
            "currency": "USD",
            "name": "PRICE LEVEL 4"
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "areas":  {
              "data":  [
                 {
                  "id": "4",
                  "type": "areas"
                },
                 {
                  "id": "8",
                  "type": "areas"
                }
              ]
            }
          }
        },
         {
          "id": "15",
          "type": "price-zones",
          "attributes":  {
            "currency": "USD",
            "name": "PRICE LEVEL 6"
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "areas":  {
              "data":  [
                 {
                  "id": "5",
                  "type": "areas"
                }
              ]
            }
          }
        },
         {
          "id": "19",
          "type": "price-zones",
          "attributes":  {
            "currency": "USD",
            "name": "PRICE LEVEL 8"
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "areas":  {
              "data":  [
                 {
                  "id": "6",
                  "type": "areas"
                }
              ]
            }
          }
        }
      ]
    },
    "areas":  {
      "data":  [
         {
          "id": "7",
          "type": "areas",
          "attributes":  {
            "rank": 0,
            "name": "BENCH4",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "20",
                  "type": "price-zones"
                },
                 {
                  "id": "23",
                  "type": "price-zones"
                }
              ]
            }
          }
        },
         {
          "id": "6",
          "type": "areas",
          "attributes":  {
            "rank": 1,
            "name": "BENCH3",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "17",
                  "type": "price-zones"
                },
                 {
                  "id": "19",
                  "type": "price-zones"
                }
              ]
            }
          }
        },
         {
          "id": "5",
          "type": "areas",
          "attributes":  {
            "rank": 2,
            "name": "BENCH2",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "13",
                  "type": "price-zones"
                },
                 {
                  "id": "15",
                  "type": "price-zones"
                }
              ]
            }
          }
        },
         {
          "id": "8",
          "type": "areas",
          "attributes":  {
            "rank": 3,
            "name": "RAMP",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "12",
                  "type": "price-zones"
                }
              ]
            }
          }
        },
         {
          "id": "22",
          "type": "areas",
          "attributes":  {
            "rank": 4,
            "name": "BENCH",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "11",
                  "type": "price-zones"
                },
                 {
                  "id": "13",
                  "type": "price-zones"
                },
                 {
                  "id": "20",
                  "type": "price-zones"
                },
                 {
                  "id": "23",
                  "type": "price-zones"
                }
              ]
            }
          }
        },
         {
          "id": "4",
          "type": "areas",
          "attributes":  {
            "rank": 5,
            "name": "BENCH1",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "11",
                  "type": "price-zones"
                },
                 {
                  "id": "12",
                  "type": "price-zones"
                }
              ]
            }
          }
        },
         {
          "id": "14",
          "type": "areas",
          "attributes":  {
            "rank": 6,
            "name": "SUPER",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "11",
                  "type": "price-zones"
                }
              ]
            }
          }
        },
         {
          "id": "2",
          "type": "areas",
          "attributes":  {
            "rank": 7,
            "name": "BOX2",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "10",
                  "type": "price-zones"
                }
              ]
            }
          }
        },
         {
          "id": "3",
          "type": "areas",
          "attributes":  {
            "rank": 8,
            "name": "BOX3",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "10",
                  "type": "price-zones"
                }
              ]
            }
          }
        },
         {
          "id": "0",
          "type": "areas",
          "attributes":  {
            "rank": 9,
            "name": "BOX",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "9",
                  "type": "price-zones"
                }
              ]
            }
          }
        },
         {
          "id": "1",
          "type": "areas",
          "attributes":  {
            "rank": 10,
            "name": "BOX1",
            "areaType": "AREA"
          },
          "relationships":  {
            "areas":  {},
            "offers":  {
              "data":  [
                 {
                  "id": "000000000001",
                  "type": "offers"
                },
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            },
            "priceZones":  {
              "data":  [
                 {
                  "id": "9",
                  "type": "price-zones"
                }
              ]
            }
          }
        }
      ]
    },
    "passwords":  {
      "data":  [
         {
          "id": "2b81df841235ca20f272acad674d6c71",
          "type": "passwords",
          "attributes":  {
            "type": "level_two_mask_rollup",
            "exclusive": false,
            "prompts":  []
          },
          "relationships":  {
            "offers":  {
              "data":  [
                 {
                  "id": "QMASK2ROLLUP",
                  "type": "offers"
                }
              ]
            }
          },
          "metadata":  {
            "type": "password-meta"
          }
        }
      ]
    }
  }
}
{% endhighlight %}


## Get Cart
{: .article .console-link #get-cart}

**Method:** GET.
Authentication required.

Returns the cart.

commerce/{version}/shopping/carts/{cartId}.{format}
{: .code .red}

### URL parameters:

| Parameter  | Description          | Type              | Default Value      | Required |
|:-----------|:---------------------|:----------------- |:------------------ |:-------- |
| `version`  | The API Version.     | string            |       "v2"         | Yes      |
| `cartId`   | Cart ID. Required.   | string            | "c5d3fb70-f7cb-489d-823d-8103222f0c17.jash1" | Yes      |
| `format`   | API Response Format. | string            |       "json"       | Yes      |

### Response structure: {# cart-response}

{: .nested-list }
- `cart` (object) - the cart
    * `id` (string) - the cart id.
    * `type` (string) - '_carts_'.
    * `attributes` (object) - the attributes of the cart.
        + `reservations` (array) - container of reservations.    
            + `{array item object}` - reservation.
        + `fees` (array) - container of order level fees.
            + `{array item object}` - order level fee.
        + `taxes` (array) - container of order level taxes.
            + `{array item object}` - order level tax.
        + `totals` (object) - the total amounts for the cart.
            + `currency` (string) - the code of the currency for the totals.
            + `price` (string) - the total price of items in the cart.
            + `fees` (string) - the total fees for the cart.
            + `taxes` (string) - the total taxes for the cart.
            + `deliveries` (string) - the total delivery costs for the cart.
            + `upsells` (string) - the total cost of upsell items in the cart.
            + `total` (string) - the grand total of the cart.
    * `relationships` (object) - the relationships of the cart. 
        + `events` (object) - container for event relationships.
            + `data` (array) - container for event relationships.
                + `{array item object}` - event reference.
                    + `id` (string) - the event id.
                    + `type` (string) - '_events_'.
        + `products` (object) - container for product relationships.
            + `data` (array) - container for product relationships.
                + `{array item object}` - the product reference.
                    + `id` (string) - the product id.
                    + `type` (string) - '_products_'.
        + `offers` (object) - container for offer relationships.
            + `data` (array) - container for offer relationships.
                + `{array item object}` - the offer reference.
                    + `id` (string) - the offer id.
                    + `type` (string) - '_offers_'.
- `_embedded` (object) - container for included (embedded) data.
    * `events` (object) - container for included events data.
        + `data` (array)
            - `{array item object}` - an event.
                * `id` (string) - the event id.
                * `type` (string) - '_events'.
                * `attributes` (object) - event attributes.
                    - `name` (string) - the event name.
                * `relationships` (object) - event relationships.
                    - `products` (object) - container for event-product relationships.
                        * `data` (array)
                            + `{array item object}` - product reference.
                                - `id` (string) - the product id.
                                - `type` (string) - '_products_'.
                    - `offers` (object) - container for event-offer relationships.
                        * `data` (array)
                            + `{array item object}` - offer refernece.
                                - `id` (string) - the offer id.
                                - `type` (string) - '_offers_'.
    * `products` (object) - container for included products data.
        + `data` (array)
            - `{array item object}` - a product.
                * `id` (string) - the product id.
                * `type` (string) - '_products_'.
                * `attributes` (object) - the product attributes.
                * `relationships` (object) - product relationships.
                    - `offers` (object) - container for product-offer relationships.
                        * `data` (array)
                            + `{array item object}` - offer reference.
                                - `id` (string) - the offer id.
                                - `type` (string) - '_offers_'.
                    - `events` (object) - container for product-event relationships.
                        * `data` (array)
                            + `{array item object}` - the event reference.
                                - `id` (string) - the event id.
                                - `type` (string) - '_events_'.
    * `offers` (object) - container for included offers data.
        + `data` (array)
            - `{array item object}` - an offer.
                * `id` (string) - the offer id.
                * `type` (string) - '_offers_'.
                * `attributes` (object) - the offer attributes.
                    + `name` (string) - the offer name.
                    + `description` (string) - the offer description.
                * `relationships` (object) - the offer relationships.
                    + `products` (object) - container for offer-product relationships.
                        * `data` (array)
                            + `{array item object}` - product reference.
                                - `id` (string) - the product id.
                                - `type` (string) - '_products_'.
                    + `events` (object) - container for offer-event relationships.
                        * `data` (array)
                            + `{array item object}` - event reference.
                                - `id` (string) - the event id.
                                - `type` (string) - '_events_'.
- `status` (string) - the Http status code for the response.

## Create Cart
{: .article .console-link #create-cart}

**Method:** POST.
Authentication required.

This operation allows users to add products to a cart.

This operation supports the following add product requests:
{: .nested-list}
* a number of items for an offer of a product.
* a number of items for an offer in specific areas.
* a number of items for an offer in a specific price range.
* a specific set of inventory items (i.e. seats).

This operation returns a new cart.

commerce/{version}/shopping/carts.{format}
{: .code .red}

### URL parameters:

| Parameter  | Description          | Type              | Default Value      | Required |
|:-----------|:---------------------|:----------------- |:------------------ |:-------- |
| `version`  | The API Version.     | string            |       "v2"         | Yes      |
| `format`   | API Response Format. | string            |       "json"       | Yes      |

### Request body structure:

{: .nested-list }
* `pollingCallbackUrl` (string) - **Required** - client webhook URI where response will be posted if the operation polls.
* `products` (array) - **Required (at least one)** - container of add product requests.
    + `{array item object}` - an add product request.
        - `product` (string) - **Required** - the product id.
        - `qty` (string) - _**Required unless** specific items (by id) are being requested_ - the number of items requested.
        - `items` (array) - _Optional_ - a list of inventory item ids.  Used to reserve specific inventory items (i.e. specific seats).
        - `offers` (array) - **Required (at least one)** - list of offer ids.  Reserved inventory will come from one of these offer ids.
            * `{array item object}` - an offer request.
                + `offer` (string) - **Required** - the offer id.
                + `code` (string) - _Optional_ - the offer code if one is required to unlock the offer.
        - `filters` (object) - _Optional_ filters to apply when searching for inventory.
            * `areas` (array) - _Optional_ - the set of areas (by id) to search for inventory.
            * `maxPrice` (string) - _Optional_ - the maximum per item price.
            * `minPrice` (string) - _Optional_ - the minimum per item price.

### Response structure:

Same as the [Get Cart API](#get-cart).


## Empty Cart
{: .article .console-link #empty-cart}

**Method:** DELETE.
Authentication required.

This operation empties the cart.

This operation returns the updated cart.

commerce/{version}/shopping/carts/{cartId}.{format}
{: .code .red}

### URL parameters:

| Parameter  | Description          | Type              | Default Value      | Required |
|:-----------|:---------------------|:----------------- |:------------------ |:-------- |
| `version`  | The API Version.     | string            |       "v2"         | Yes      |
| `cartId`   | Cart ID. Required.   | string            | "c5d3fb70-f7cb-489d-823d-8103222f0c17.jash1" | Yes      |
| `format`   | API Response Format. | string            |       "json"       | Yes      |

### Response structure:

Same as the [Get Cart API](#get-cart).



## Update Cart Products
{: .article .console-link #update-cart-products}

**Method:** PATCH
Authentication required.

This operation allows users to add or remove products to/from a cart.

This operation supports add products in the same ways as the [Create Cart Operation](#create-cart).

This operation supports the following removal requests:
{: .nested-list}
* all items in a reservation.
* all items in a reservation for a specific product.
* all items in a specified set of inventory item groups.
* a set of specified inventory items.

This operation returns the updated cart.

commerce/{version}/shopping/carts/{cartId}/products.{format}
{: .code .red}

### URL parameters:

| Parameter  | Description          | Type              | Default Value      | Required |
|:-----------|:---------------------|:----------------- |:------------------ |:-------- |
| `version`  | The API Version.     | string            |       "v2"         | Yes      |
| `cartId`   | Cart ID. Required.   | string            | "c5d3fb70-f7cb-489d-823d-8103222f0c17.jash1" | Yes      |
| `format`   | API Response Format. | string            |       "json"       | Yes      |


### Request body structure:

{: .nested-list }
* `pollingCallbackUrl` (string) - **Required** - client webhook URI where response will be posted if the operation polls.
* `products` (array) - **Required (at least one)** - container of update product requests.
    + `{array item object}` - an update product request.
        - `op` (string) - **Required** - the operation code.  valid values - _add_, _remove_.
        - `product` (string) - **Required when adding or removing a product** - the product id.
        - `qty` (string) - _**Required when adding a product unless** specific items (by id) are being requested_ - the number of items requested.
        - `items` (array) - _Optional_ - a list of inventory item ids.  Used to add/remove specific items (i.e. seats).
        - `offers` (array) - **Required when adding a product** - list of offer ids.  Reserved inventory will come from one of these offer ids.
            * `{array item object}` - an offer request.
                + `offer` (string) - **Required** - the offer id.
                + `code` (string) - _Optional_ - the offer code if one is required to unlock the offer.
        - `filters` (object) - _Optional_ filters to apply when searching for inventory.
            * `areas` (array) - _Optional_ - the set of areas (by id) to search for inventory.
            * `maxPrice` (string) - _Optional_ - the maximum per item price.
            * `minPrice` (string) - _Optional_ - the minimum per item price.
        - `reservation` (string) - _Optional_ - the reservation to remove from the cart.
        - `itemGroups` (array) - _Optional_ - list of item group ids to remove from the cart.

### Response structure:

Same as the [Get Cart API](#get-cart).



## Select Payments
{: .article .console-link #select-payments}

**Method:** PATCH
Authentication required.

This operation allows users to add one or more payments to a cart.

This operation returns a cart with the selected payment(s).

commerce/{version}/shopping/carts/{cartId}/payments.{format}
{: .code .red}

### URL parameters:

| Parameter  | Description          | Type              | Default Value      | Required |
|:-----------|:---------------------|:----------------- |:------------------ |:-------- |
| `version`  | The API Version.     | string            |       "v2"         | Yes      |
| `cartId`   | Cart ID. Required.   | string            | "c5d3fb70-f7cb-489d-823d-8103222f0c17.jash1" | Yes      |
| `format`   | API Response Format. | string            |       "json"       | Yes      |


### Request body structure:

{: .nested-list }
* `pollingCallbackUrl` (string) - **Required** - client webhook URI where response will be posted if the operation polls.
* `payments` (array) - **Required (at least one)** - container of add payment requests.
    + `{array item object}` - an add payment request.
        - `type` (string) - **Required** - the payment type.  valid values - _cash_, _wallet_.
        - `amount` (object) - **Required** - the payment amount object.
            * `amount` (string) - **Required** - the payment amount.
            * `currency` (string) - **Required** - the payment currency.
        - `token` (string) - _**Required when wallet payment**_ - the wallet token.
        - `cvv` (string) - _**Required when wallet payment**_ - the cvv associated with wallet.
        - `selectedItems` (array) - _Optional_ - list of the selected items to which this payment applies.
            * `{array item object}` - a selected payment item.
                + `reservations` (array) - **Required** - list of the reservation ids.

### Response structure:

Same as the [Get Cart API](#get-cart).