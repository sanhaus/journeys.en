---
title: Configuring the data source
description: Learn how to configure the data source for journey advanced use case
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: journeys
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: n
internal: n
snippet: y
---

# Configuring the data sources{#concept_vml_hdy_w2b}

In our use case, we want to use personalization data for our messages. We also need to check if the person is a loyalty member and has not been contacted in the last 24 hours. This information is stored in the Unified Profile database. The **technical user** needs to configure the Experience Platform data source to retrieve those fields.

For additional information on data source configuration, refer to [](../datasource/ds.md#concept_s1s_dqt_52b).

1. In the top bar, click **Data Sources** and select the build-in Experience Platform data source.

    ![](../assets/journey23.png)

1. In the pre-configured group fields, check that the following fields are selected:

    * _person > name > firstName_
    * _person > name > lastName_
    * _personalEmail > address_

1. Click **Add a New Field Group**, select a **Profiles** schema and add the **Loyalty member** field for our condition. The **Loyalty member** field is a custom field and was added in XDM: __customer > marlton > loyaltyMember_

    ![](../assets/journeyuc2_6.png)

1. Click **Add a New Field Group**, select an **ExperienceEvent** schema and choose the fields needed for our condition on the number of messages sent in a given period: _timestamp_ for the date and _directMarketing > sends > value_ for the number of messages sent.

    ![](../assets/journeyuc2_7.png)

1. Click **Save**.

We also need to check if the person has a reservation in the hotel reservation system. The **technical user** needs to configure a second data source to retrieve this field.

1. In the list of data sources, click **Add** to add a new external data source to define the connection to your hotel reservation system.

    ![](../assets/journeyuc2_9.png)

1. Enter a name for your data source and the URL of the external service, for example: [https://marlton.com/reservation](https://marlton.com/reservation)

    >[!CAUTION]
    >
    >We strongly recommend using HTTPS for security reasons.

1. Configure the authentication depending on the external service configuration: **No authentication**, **Basic** or **API key**. In our example, we choose "Basic" for the type and specify the username and password for the API call.

    ![](../assets/journeyuc2_10.png)

1. Click **Add a New Field Group** to define the information to be retrieved and the API parameters. For our example, there is only one parameter (the id), so we need to create one field group with the following information:

    * **Method**: select the POST or GET method. In our case, we select the GET method.
    * **Cache duration**: this varies according to the frequency of the API calls. In our case, the reservation system is updated every 10 minutes.
    * **Response Payload**: click inside the **Payload** field and paste an example of the payload. Verify that the field types are correct. Each time the API is called, the system will retrieve all the fields included in the payload example. In our example, the payload only contains the reservation status:

        ```
    {
        "reservation" : true
    }
        ```

    * **Dynamic Values**: enter the parameter corresponding to the key used to identify each customer, "id" in our example. The value of this parameter will be defined in the journey.

    ![](../assets/journeyuc2_11.png)

1. Click **Save**.

    The data sources are now configured and ready to be used in your journey.