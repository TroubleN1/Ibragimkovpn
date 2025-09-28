# IbragimkoVPN (WireGuard userspace skeleton)

**Важно:** этот проект поднимается и собирается в Android Studio.
Для реального подключения вам нужно добавить бинарники `wireguard-go` по ABI в `app/src/main/assets/wireguard/<ABI>/wireguard-go`.
Примеры ABI: `arm64-v8a`, `armeabi-v7a`, `x86_64`, `x86`.

## Шаги сборки
1. Откройте папку в Android Studio (Giraffe+).
2. Подождите Gradle sync, затем `Run` для запуска на устройстве.
3. Перед первым запуском замените в `app/src/main/assets/client1.conf` ключи и адреса на ваши.
4. Скопируйте `wireguard-go` бинарники под ваш ABI в `app/src/main/assets/wireguard/<ABI>/wireguard-go` и сделайте их исполняемыми, если собираете вручную.
   - Бинарники можно собрать из исходников WireGuard или взять из вашего CI/репозитория.
5. На устройстве включите Always-on + Lockdown для kill-switch (в системных настройках VPN).

## Примечания
- Этот skeleton демонстрирует userspace WireGuard через `VpnService`.
- Для продакшена добавьте: reconnection/backoff, split tunneling, обработку IPv6, DoH/DoT, UI со списком серверов.
