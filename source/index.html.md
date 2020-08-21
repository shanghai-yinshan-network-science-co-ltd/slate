---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - python
  - java

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Pyxis credit scoring provids you powerfull ability of risk control with behavior data.

This documentaion helps you to make a simple HTTP request from the very benining. 

# Credit Scoring

<aside class="notice">
Make sure you have your right <code>personal API key</code>.
</aside>

## behavior scoring

```python
import izi

api = credit_scoring.client('YOUR_ACCESS_KEY', 'YOUR_SECRET_KEY')
data = {
  "name": "NAME",
  "credential_number": "317xxxxxxxxxxxx",
  "mobile": "08xxxxxxxxx",
  "gender": "MALE",
  "marital_status": "SINGLE",
  "last_education": "S1",
  "profession": "xxx",
  "salary": "BELOW_6B",
  "logs": [
    {
      "action_type": "click_event",
      "end_time": "2019-12-02 11:36:26.182",
      "log_id": "20191202113501672_1_61",
      "log_source": "native",
      "log_time": "2019-12-02 11:36:26.182",
      "page_id": "view.certification.ProfessionalInfoActivity",
      "runId": "20191202113501672_1",
      "start_time": "2019-12-02 11:36:26.182",
      "view_path": "ProfessionalInfoActivity-FL-LL[0]-SV[1]-LL[0]-LL[1]-LL[1]"
    },
    {
      "action_type": "click_event",
      "end_time": "2019-12-02 11:36:50.177",
      "log_id": "20191202113501672_1_62",
      "log_source": "native",
      "log_time": "2019-12-02 11:36:50.177",
      "page_id": "view.certification.ProfessionalInfoActivity",
      "runId": "20191202113501672_1",
      "start_time": "2019-12-02 11:36:50.177",
      "view_path": "ProfessionalInfoActivity-DV-FL[0]-FL[0]-AlertDlgLayout[0]-FL[2]-FL[0]-LL[0]-LV[0]-LL[12]-RL[0]"
    }
  ]
 }
url = "https://api.pyxis.credit/v3/check"
response = api.request(url, data)
print(response)
```

```java
import java.util.HashMap;
import java.util.Map;
import credit.izi.Client;

public class MainClass {
    public static void main(String[] args) {
        Client api = new Client("YOUR_ACCESS_KEY", "YOUR_SECRET_KEY");
        CheckRequest req = new CheckRequest();
        
        req.setName("NAME");
        req.setCredential_number("317xxxxxxxxxxxx");
        req.setMobile("08xxxxxxxxx");
        req.setGender("MALE");
        req.setMarital_status("SINGLE");
        req.setLast_education("S1");
        req.setProfession("xxx");
        req.setsalary("BELOW_6B");

        List<EventLog> logs = new LinkedList();
        EventLog log = new EventLog();
        log.setAction_type("click_event");
        log.setEnd_time("2019-12-02 11:36:26.182");
        log.setLog_id("20191202113501672_1_61");
        log.setLog_source("native");
        log.setLog_time("2019-12-02 11:36:26.182");
        log.setPage_id("view.certification.ProfessionalInfoActivity");
        log.setRunId("20191202113501672_1");
        log.setStart_time("2019-12-02 11:36:26.182");
        log.setView_path("ProfessionalInfoActivity-FL-LL[0]-SV[1]-LL[0]-LL[1]-LL[1]");
        logs.add(log);
        req.setLogs(log);
        
        String url = "https://api.pyxis.credit/v3/check";
        CheckResponse response = api.Request(url, req);
        System.out.println(response);
    }
}
```

> The above command returns JSON structured like this:

```json
{
  "status": "OK",
  "score": 800
}
```

This endpoint retrieves all kittens.

### HTTP Request

`POST https://api.pyxis.credit/v3/check`

### CheckRequest

Parameter | Default | Description
--------- | ------- | -----------
name| false | Name of the customer.
credential_number| false | Nik number of the customer.
mobile| false | Mobile number of the customer.
gender| false | Gender of the customer.
marital_status| false | DIVORCED/MARRIED/SINGLE/WIDOWED.
last_education| false | BACHELOR/ELEMENTARY/JUNIOR_HIGH_SCHOOL/MASTER/NOT_EDUCATED/PHD/SENIOR_HIGH_SCHOOL/VOCATIONAL
profession| false | BPO_PROFESSIONALS/BROKERS/BUSINESS_OWNER/CONTRACT_EMPLOYEE/DISTRIBUTOR/EXECUTIVE/FOOD_INDUSTRY/FREELANCE/GOVERNMENT_EMPLOYEE/HOUSEWIFE/HOUSE_WIFE/INFORMAL_WORKERS/IT/LABORER/MARKETING/MEDICAL_PERSONNEL/OFFICE_STAFF/PRIVATE_COMPANY_EMPLOYEE/PROFESSIONAL_WORKER/SALES_STAFF/SELF_EMPLOYED/STAFF_OR_FACTORY_WORKER/TEACHER/UNEMPLOYED
salary| false | BELOW_6B/BETWEEN_10B_15B/BETWEEN_15B_20B/BETWEEN_20B_30B/BETWEEN_6B_10B/OVER_30B
logs| false | Event logs.

### EventLog

Parameter | Default | Description
--------- | ------- | -----------
action_type| false | Action type of this event.
start_time| false | The start time of the session.
end_time| false | The end time of the session.
log_id| false | Every event log has an unique id.
log_source| false | Where is this event generated from. Usually should be native for the android device.
log_time| false | Create time of this log.
page_id| false | Page id of app.
runId| false | Unique id for the whole session.
view_path| false | UI path to the widget.
