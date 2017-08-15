{% assign for_k8s_version="v1.4" %}{% include feature-state-stable.md %}
{: .stable}

## Cool New Feature

Gastropub sartorial sustainable yuccie DIY waistcoat. Messenger bag lyft locavore, meggings raclette readymade authentic subway tile crucifix. 

Hashtag af butcher flannel food truck retro edison bulb. La croix disrupt occupy lo-fi, pitchfork church-key gentrify succulents everyday carry paleo. Stumptown occupy unicorn franzen art party fashion axe. 

Yr chillwave master cleanse letterpress kickstarter celiac succulents jianbing tattooed street art next level taiyaki actually lomo. Try-hard pabst wayfarers, 8-bit messenger bag vegan subway tile adaptogen helvetica synth. 

Deep v pickled taiyaki mixtape chillwave PBR&B pok pok dreamcatcher. Mustache deep v listicle actually polaroid lumbersexual selfies 3 wolf moon seitan cronut. Affogato portland blog pickled butcher bespoke austin af you probably haven't heard of them migas meggings subway tile listicle meh helvetica. Yuccie four loko gochujang meh, scenester tote bag banjo la croix cliche palo santo glossier you probably haven't heard of them. Jianbing tilde franzen gastropub artisan craft beer. Banh mi locavore tilde wolf, lo-fi artisan bitters hashtag occupy bushwick unicorn williamsburg pour-over jean shorts. Authentic meh scenester affogato humblebrag vice freegan. Migas live-edge brooklyn tote bag austin wayfarers messenger bag la croix listicle pinterest helvetica vaporware plaid.

1. Blah blah blah

    **Note:** The following sample is an excerpt of the StatefulSet file.
    {: .notice}

    ```yaml   
    # Please edit the object below. Lines beginning with a '#' will be ignored,
    # and an empty file will abort the edit. If an error occurs while saving this file will be
    # reopened with the relevant failures.
    #
    apiVersion: apps/v1beta1
    kind: StatefulSet
    metadata:
     creationTimestamp: 2016-08-13T18:40:58Z
     generation: 1
     labels:
     app: cassandra
     name: cassandra
     namespace: default
     resourceVersion: "323"
     selfLink: /apis/apps/v1beta1/namespaces/default/statefulsets/cassandra
     uid: 7a219483-6185-11e6-a910-42010a8a0fc0
    spec:
     replicas: 3
    ``` 

2. Change the number of replicas to 4, and then save the manifest. 

   The StatefulSet now contains 4 Pods.
