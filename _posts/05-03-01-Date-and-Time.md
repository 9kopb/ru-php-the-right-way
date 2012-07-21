---
title: ���� � �����
isChild: true
---

## ���� � �����

PHP ����� ���������� ����� � ��������� DateTime, �� ������� ���, ����� ��� ����� ��������, ��������, �������� ��� ��������� ���� ��� �����.
���-�� � PHP ����� �������, ��������� � ����� � ��������, ������ ������ DateTime, �� ����� ������������� ������� ��������-��������������� ��������� ��� ������� ����������� �����.
�� ����� ������������ ��������� ����, �� ��� �� ��������� ����� ��������� ��������.

��� ������ ������ � DateTime, �������������� "�����" ������ ���� � ������� � ������ � ������� ���������� ������ `createFromFormat()` ��� ��������� `new \DateTime`, ����� �������� ������� ���� � �����. ����������� ����� `format()` ��� ��������������� DateTime ������� � ������ ��� ������.
 
{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = \DateTime::createFromFormat('d. m. Y', $raw);

echo "Start date: " . $start->format('m/d/Y') . "\n";
{% endhighlight %}

���������� � DateTime �������� � �������������� ������ DateInterval. � ������ DateTime ���� ������ `add()` � `sub()`, ������� ��������� DateInterval, ��� ��������. �� ������ ���, ������� ������� ���������� ����� ������ ������ ����, ������� ����� � ����� ������� ������ �������� ��� �������������. ������ ����� ����������� ��������� ���. ��� ������� ������� ����� ������ ����������� ����� `diff()`. �� ������ ����� ������ DateInterval, ������� ����� ����� ����������. 

{% highlight php %}
<?php
// ������� ����� $start � ��������� 1 ����� � 6 ����.
$end = clone $start;
$end->add(new \DateInterval('P1M6D'));

$diff = $end->diff($start);
echo "Difference: " . $diff->format('%m �����, %d ���� (�����: %a ����)') . "\n";
// �������: 1 �����, 6 ���� (�����: 37 ����)
{% endhighlight %}

� ��������� DateTime, �� ������ ������������ ����������� ������ ���������:
{% highlight php %}
<?php
if($start < $end) {
    echo "Start ����� End!\n";
}
{% endhighlight %}

� ��������� ������, ��� ������������ ������ DatePeriod. �� ������������ ��� �������� ������������� �������. �� ����� ��������� ��� ������� DateTime, ������ � �����, � �������� ��� �������� �� ������ ��� ������� ����� ����.

{% highlight php %}
<?php
// ����� ���� ��������� ����� $start � $end
$periodInterval = \DateInterval::createFromDateString('first thursday');
$periodIterator = new \DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach($periodIterator as $date)
{
    // ����� ������ ���� � �������
    echo $date->format('m/d/Y') . " ";
}
{% endhighlight %}

* [��������� � DateTime][datetime]
* [��������� � DateInterval][dateinterval]
* [��������� � DatePeriod][dateperiod]
* [��������� � �������������� ����][dateformat] (�������� ������� ������� ������ ����)

[datetime]: http://www.php.net/manual/class.datetime.php
[dateinterval]: http://www.php.net/manual/class.dateinterval.php
[dateperiod]: http://www.php.net/manual/class.dateperiod.php
[dateformat]: http://www.php.net/manual/function.date.php
