# Which day is today

```yaml
Today is {{ ['Monday','Tuesday','Wednesday','Thursday','Friday','Saturday','Sunday'][now().weekday()] }}
Today is {{ now().strftime('%A') }}
```

# string to weekday

```yaml
{{ (strptime('1-5-2023','%d-%m-%Y')|as_local).weekday() }}
```

# Check how many lights are activitated at this moment.

```yaml
{% set array = [
  states.light.kerstmis_huis_een,
  states.light.kerstmis_huis_twee,
  states.light.edith_nachtlamp,
  states.light.hans_nachtlamp,
  states.light.woonkamer_lamp_2,
  states.light.woonkamer_lamp_1,
  states.light.tv_led,
  states.light.chelenne_led_rand,
  states.light.vanity_mirror,
  states.switch.hal_schakelaar,
  states.switch.hal_schakelaar_carport,
  states.switch.badkamer_plafond,
  states.switch.chelenne_plafondlamp,
  states.switch.lavalamp,
  states.switch.stefan_plafondlamp,
  states.switch.voortuin_lamp,
  states.switch.woonkamer_lamp,
  states.switch.woonkamer_bureaulamp,
  states.switch.eetkamer_plafondlamp,
  states.switch.keuken_licht,
  states.switch.achtertuin_lampen,
  states.switch.overkapping,
  states.switch.achtertuin_muurspots,
  states.switch.masterbedroom_plafondlamp,
  states.switch.masterbedroom_tafellamp,
  states.switch.toilet_plafondlamp,
  states.switch.kerstboom,
  states.switch.kerstverlichting_ijspegel_voortuin
  ] %}
{% set amount = array | selectattr('state', 'defined') | selectattr('state','eq','on') | list | count %}

{% if amount > 0 %}
  {{ amount }} lampen geactiveerd.
{% endif %}
```
