# Pick

Filter a map by the specified list of keys. Map is returned with the key in the order of the pick list.

Similarly, you can filter a map by the specified list of indices.

{% hint style="warning" %}
Note that versions prior to 4.18 require the 'eval/e' command to be specified.&#x20;

`yq e <exp> <file>`
{% endhint %}

## Pick keys from map
Note that the order of the keys matches the pick order and non existent keys are skipped.

Given a sample.yml file of:
```yaml
myMap:
  cat: meow
  dog: bark
  thing: hamster
  hamster: squeek
```
then
```bash
yq '.myMap |= pick(["hamster", "cat", "goat"])' sample.yml
```
will output
```yaml
myMap:
  hamster: squeek
  cat: meow
```

## Pick indices from array
Note that the order of the indexes matches the pick order and non existent indexes are skipped.

Given a sample.yml file of:
```yaml
- cat
- leopard
- lion
```
then
```bash
yq 'pick([2, 0, 734, -5])' sample.yml
```
will output
```yaml
- lion
- cat
```
