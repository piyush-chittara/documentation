# Client APIs

* Verify Redeem Code\
  \
  Redeem Coupon/QR code where codes are system generated for an utility

{% swagger src="../../.gitbook/assets/swagger.yml" path="/verify" method="post" %}
[swagger.yml](../../.gitbook/assets/swagger.yml)
{% endswagger %}

* Get All Benefits of Collection\
  \
  Get all benefits present on a collection address

{% swagger src="../../.gitbook/assets/swagger.yml" path="/collection/{address}" method="get" %}
[swagger.yml](../../.gitbook/assets/swagger.yml)
{% endswagger %}

* Get Claimed Users of an Utility\
  \
  Get all claimed users for custom codes provided

{% swagger src="../../.gitbook/assets/swagger.yml" path="/claims/{utilityId}" method="get" %}
[swagger.yml](../../.gitbook/assets/swagger.yml)
{% endswagger %}
