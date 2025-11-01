# GFX4dESP32 Library - 4D Systems Display Driver
# Supports ESP32-S3 gen4 displays

idf_component_register(
    SRCS 
        # Core library
        "src/gfx4desp32.cpp"
        
        # RGB Panel base classes (for 90CT)
        "src/gfx4desp32_rgb_panel.cpp"
        "src/gfx4desp32_rgb_panel_t.cpp"
        "src/gfx4desp32_rgb_panel_rt.cpp"
        
        # ESP32-S3 9" Display (90CT) - 800x480
        "src/gfx4desp32_ESP32_90CT.cpp"
        
        # Touch support
        "src/gfx4desp32_touch.cpp"
        
        # RTC support
        "src/gfx4desp32_rtc.cpp"
    
    INCLUDE_DIRS 
        "src"
    
    REQUIRES 
        espressif__arduino-esp32
        esp_lcd
        driver
    
    PRIV_REQUIRES
        esp_driver_gpio
        esp_driver_i2c
        esp_driver_spi
        esp_psram
)

# Suppress uninitialized variable warnings for this library
# The library has many false positives where variables are initialized conditionally
target_compile_options(${COMPONENT_LIB} PRIVATE -Wno-maybe-uninitialized -Wno-misleading-indentation)

