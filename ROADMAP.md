# adapters Yol Haritası

## Faz 0: Sözleşmeler (davet öncesi)

- [ ] Go modül yapısı (`ports/`, `oidc/`, `s3/`, `smtp/`, …), CI (gofmt, go vet, golangci-lint, `go test -race`)
- [ ] `ports` ilk taslak: `IdentityProvider`, `ObjectStorage`, `EmailSender`
- [ ] Sözleşme testi altyapısı: her adapter aynı test paketini geçmeli
- [ ] Adapter yazma rehberi

## Faz 1: Çekirdek Adapterler

- [ ] OIDC/Keycloak adapteri ve fake uygulaması
- [ ] S3/MinIO adapteri (imzalı URL, içerik tipi kontrolü)
- [ ] SMTP adapteri, gönderim durumu takibi
- [ ] `ports` 0.1 sürümü

## Faz 3: LMS ve Bildirim

- [ ] Jitsi adapteri: JWT ile moderatör/katılımcı, oda yaşam döngüsü
- [ ] Jibri kayıt tetikleme ve VOD işleme için arayüz (işleme hattı sınırı)
- [ ] BigBlueButton adapteri: oda yönetimi, rol bazlı katılım bağlantısı, kayıt listesi ([#5](https://github.com/Libre-University/adapters/issues/5))
- [ ] `LiveClassroom` portuna yetenek bilgisi (gömme, grup odaları, kayıt) eklenmesi
- [ ] Push bildirim adapteri

## Faz 4+: Kamu ve Finans

- [ ] Banka sanal POS (açık sözleşmeli, sağlayıcı değiştirilebilir)
- [ ] e-Devlet, YÖKSİS, ÖSYM, KEP/e-imza adapterleri
- [ ] Mevcut LDAP/Active Directory dizinlerinden kullanıcı içe aktarımı
