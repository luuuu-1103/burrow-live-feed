key is how to read chain data

in this case, how to read burrow contract data

# Functionalities
single page 
    live borrow event
    can filter liquidation event only
    can filter by account

only show most recent x blocks

# How does it work
based on websocket
there's an indexing server 
https://github.com/evgenykuzyakov/event-api
https://thewiki.near.page/events-api

use wscat
```
wscat -c 'wss://events.near.stream/ws'
```

send msg
```
{
   "secret":"brrr",
   "filter":{
      "status":"SUCCESS",
      "account_id":"contract.main.burrow.near",
      "event":{
         "standard":"burrow",
         "event":"liquidate"
      }
   },
   "fetch_past_events":1
}
```

receive msg
```
"20":"24":"00":{
   "secret":"brrr",
   "events":[
      {
         "block_height":"68098673",
         "block_hash":"8GYJSqYDDW7vwaSFEoot1N5bdCe1RMS6wcuxSeGZ7eQf",
         "block_timestamp":"1655692237012178438",
         "block_epoch_id":"BCiXbp8xLtas7RSEbTmZAsW8cRBJnQa6CcyN7GmsGArm",
         "receipt_id":"4jnifzRzibArXFe47VSPfoH7awuBahmXSUbDmoXgqbok",
         "log_index":3,
         "predecessor_id":"priceoracle.near",
         "account_id":"contract.main.burrow.near",
         "status":"SUCCESS",
         "event":{
            "standard":"burrow",
            "version":"1.0.0",
            "event":"liquidate",
            "data":[
               {
                  "account_id":"thankyouser.near",
                  "liquidation_account_id":"odranoelzerep.near",
                  "collateral_sum":"36.930896572127488365435",
                  "repaid_sum":"36.5586047267533242662238"
               }
            ]
         }
      }
   ],
   "note":"past"
}
```