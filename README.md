# adapters

LibreUniversity dış sistem entegrasyonları ([ADR-0007](https://github.com/Libre-University/docs/blob/main/docs/adr/0007-isolate-external-systems-with-adapters.md)).

## Yapı

- `libre-ports`: bağımlılıksız, versiyonlanan arayüz paketi (Python `Protocol` tanımları ve ortak veri tipleri). `platform-api` yalnızca bu paketi bilir.
- Adapter paketleri: her biri bir port'u uygular ve Python entry point ile kaydolur. Hangi adapterin kullanılacağı yapılandırmayla seçilir.
- Her adapter için sahte (fake) uygulama ve sözleşme testleri bulunur; böylece dış sistem olmadan geliştirme yapılabilir.

## Adapterler

| Port | Adapter | Faz |
| --- | --- | --- |
| `IdentityProvider` | OIDC (Keycloak) | 1 |
| `ObjectStorage` | S3 uyumlu (MinIO) | 1 |
| `EmailSender` | SMTP | 1 |
| `LiveClassroom` | Jitsi (JWT) | 3 |
| `PushSender` | UnifiedPush / genel | 3 |
| `PaymentGateway` | Banka sanal POS | 4 |
| `GovernmentIdentity` | e-Devlet | 4 |
| `AcademicRegistry` | YÖKSİS | 4 |

## Fazlara Göre İşler

| Faz | Bu repoda yapılacaklar |
| --- | --- |
| Faz 0 | `libre-ports` arayüz paketi taslağı, sözleşme testi altyapısı, adapter yazma rehberi |
| Faz 1 | OIDC/Keycloak, S3/MinIO ve SMTP adapterleri; `libre-ports` 0.1 |
| Faz 2 | Çekirdek adapterlerin sertleştirilmesi (Faz 2'de yeni adapter yok) |
| Faz 3 | Jitsi (JWT), Jibri kayıt arayüzü, push bildirim adapterleri |
| Faz 4+ | Banka sanal POS, e-Devlet, YÖKSİS, ÖSYM, KEP/e-imza, LDAP/AD içe aktarımı |

Ayrıntılı ve işaretlenebilir liste: [ROADMAP.md](ROADMAP.md). Fazlar [ana yol haritası](https://github.com/Libre-University/docs/blob/main/ROADMAP.md) ile hizalıdır. Açık işler için `phase:*` etiketlerine bakın.

## Katkı

Katkı rehberi, davranış kuralları ve güvenlik politikası organizasyon genelinde [`.github`](https://github.com/Libre-University/.github) reposundadır. Mimari kararlar [`docs`](https://github.com/Libre-University/docs) reposundaki ADR'lerle alınır.

## Lisans

Bu proje [GNU Affero Genel Kamu Lisansı v3.0 veya sonrası](LICENSE) (AGPL-3.0-or-later) ile lisanslanmıştır. Ağ üzerinden hizmet olarak sunulan değiştirilmiş sürümlerin kaynak kodu da kullanıcılarla paylaşılmalıdır ([ADR-0002](https://github.com/Libre-University/docs/blob/main/docs/adr/0002-prefer-agpl-3-or-later-license.md)).
