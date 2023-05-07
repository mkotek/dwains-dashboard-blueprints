- platform: template
  sensors:
    car_tire_pressure_rear_left:
      friendly_name: Tire pressure Rear Left
      value_template: '{{ states.binary_sensor.$license$_tire_warning.attributes.tirepressureRearLeft }}'
    car_tire_pressure_rear_right:
      friendly_name: Tire pressure Rear Right
      value_template: '{{ states.binary_sensor.$license$_tire_warning.attributes.tirepressureRearRight }}'
    car_tire_pressure_front_left:
      friendly_name: Tire pressure Front Left
      value_template: '{{ states.binary_sensor.$license$_tire_warning.attributes.tirepressureFrontLeft }}'
    car_tire_pressure_front_right:
      friendly_name: Tire pressure Front Right
      value_template: '{{ states.binary_sensor.$license$_tire_warning.attributes.tirepressureFrontRight }}'
    car_rangeliquid:
      friendly_name: Car liquid range
      value_template: '{{ states.sensor.$license$_range_liquid }}'
    car_service_days:
      friendly_name: Car service days
      value_template: '{{ states.sensor.$license$_odometer.attributes.serviceintervaldays }}'
    
    car_lock_front_right:
      friendly_name: Lock Front Right
      value_template: >-
        {% if is_state_attr('sensor.$license$_lock', 'doorlockstatusfrontright', false)%}
            Closed
        {% else %}
            Open
        {% endif %}
      icon_template: >
        {% if is_state_attr('sensor.$license$_lock', 'doorlockstatusfrontright', false)%}
          mdi:lock-outline
        {% else %} 
          mdi:lock-open-variant-outline
        {% endif %}

    car_lock_front_left:
      friendly_name: Lock Front Left
      value_template: >-
        {% if is_state_attr('sensor.$license$_lock', 'doorlockstatusfrontleft', false)%}
            Closed
        {% else %}
            Open
        {% endif %}
      icon_template: >
        {% if is_state_attr('sensor.$license$_lock', 'doorlockstatusfrontleft', false)%}
          mdi:lock-outline
        {% else %} 
          mdi:lock-open-variant-outline
        {% endif %}

    car_lock_rear_right:
      friendly_name: Lock Rear Right
      value_template: >-
        {% if is_state_attr('sensor.$license$_lock', 'doorlockstatusrearright', false)%}
            Closed
        {% else %}
            Open
        {% endif %}
      icon_template: >
        {% if is_state_attr('sensor.$license$_lock', 'doorlockstatusrearright', false)%}
          mdi:lock-outline
        {% else %} 
          mdi:lock-open-variant-outline
        {% endif %}

    car_lock_rear_left:
      friendly_name: Lock Rear Left
      value_template: >-
        {% if is_state_attr('sensor.$license$_lock', 'doorlockstatusrearleft', false)%}
            Closed
        {% else %}
            Open
        {% endif %}
      icon_template: >
        {% if is_state_attr('sensor.$license$_lock', 'doorlockstatusrearleft', false)%}
          mdi:lock-outline
        {% else %} 
          mdi:lock-open-variant-outline
        {% endif %}

    car_lock_trunk:
      friendly_name: Lock trunk
      value_template: >-
        {% if is_state_attr('sensor.$license$_lock', 'decklidstatus', false)%} 
            Closed
        {% else %}
            Open
        {% endif %}
      icon_template: >
        {% if is_state_attr('sensor.$license$_lock', 'decklidstatus', false)%} 
          mdi:lock-outline
        {% else %}
          mdi:lock-open-variant-outline
        {% endif %}

    car_lock_hood:
      friendly_name: Lock hood
      value_template: >-
        {% if is_state_attr('sensor.$license$_lock', 'hoodStateRollup', false)%} 
            Closed
        {% else %}
            Open
        {% endif %}
      icon_template: >
        {% if is_state_attr('sensor.$license$_lock', 'hoodStateRollup', false)%} 
          mdi:lock-outline
        {% else %}
          mdi:lock-open-variant-outline
        {% endif %}

    car_window_front_left:
      friendly_name: Window Front Left
      value_template: >-
        {% if is_state_attr('binary_sensor.$license$_windows_closed', 'windowstatusfrontleft', '2')%} 
            Closed
        {% else %}
            Open
        {% endif %}
      icon_template: >
        {% if is_state_attr('binary_sensor.$license$_windows_closed', 'windowstatusfrontleft', '2')%} 
          mdi:window-closed
        {% else %}
          mdi:window-open
        {% endif %}

    car_window_front_right:
      friendly_name: Window Front Right
      value_template: >-
        {% if is_state_attr('binary_sensor.$license$_windows_closed', 'windowstatusfrontright', '2')%} 
            Closed
        {% else %}
            Open
        {% endif %}
      icon_template: >
        {% if is_state_attr('binary_sensor.$license$_windows_closed', 'windowstatusfrontright', '2')%} 
          mdi:window-closed
        {% else %}
          mdi:window-open
        {% endif %}

    car_window_rear_left:
      friendly_name: Window Rear Left
      value_template: >-
        {% if is_state_attr('binary_sensor.$license$_windows_closed', 'windowstatusrearleft', '2')%} 
            Closed
        {% else %}
            Open
        {% endif %}
      icon_template: >
        {% if is_state_attr('binary_sensor.$license$_windows_closed', 'windowstatusrearleft', '2')%} 
          mdi:window-closed
        {% else %}
          mdi:window-open
        {% endif %}

    car_window_rear_right:
      friendly_name: Window Rear Right
      value_template: >-
        {% if is_state_attr('binary_sensor.$license$_windows_closed', 'windowstatusrearright', '2')%} 
            Closed
        {% else %}
            Open
        {% endif %}
      icon_template: >
        {% if is_state_attr('binary_sensor.$license$_windows_closed', 'windowstatusrearright', '2')%} 
          mdi:window-closed
        {% else %}
          mdi:window-open
        {% endif %}
        
    car_window_sunroof:
        friendly_name: Window Sunroof
        value_template: >-
          {% if is_state_attr('sensor.$license$_lock', 'sunroofstatus', '0')%} 
            Closed
          {% else %}
            Open
          {% endif %}
        icon_template: >
          {% if is_state_attr('sensor.$license$_lock', 'sunroofstatus', '0')%} 
            mdi:checkbox-blank-circle-outline
          {% else %}
            mdi:checkbox-marked-circle-outline
          {% endif %}
          
    my_car_lock_status:
        friendly_name: Car Lock
        value_template: >-
          {% if is_state('sensor.$license$_lock', '0') %}
            Open
          {% elif is_state('sensor.$license$_lock', '1') %}
            Internally closed
          {% elif is_state('sensor.$license$_lock', '2') %}
            Externally closed
          {% elif is_state('sensor.$license$_lock', '3') %}
            Selection opened
          {% else %}
            Unknown
          {% endif %}
        icon_template: >
          {% if is_state('sensor.$license$_lock', '0') %}
            mdi:lock-open-variant-outline
          {% else %}
            mdi:lock-outline
          {% endif %}
