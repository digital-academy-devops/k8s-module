# Модуль 7. Контейнерная оркестрация с Kubernetes.

Целью данного модуля является реализация развертывания тестового приложения в Kubernetes.

## Предварительные требования

Предполагается, что Вы: 
- Выполнили задания по модулю [Terraform](https://github.com/digital-academy-devops/terraform-module), понимаете принципы организации репозитория [terraform-gitops](https://github.com/digital-academy-devops/terraform-gitops) и работы с ним;
- Выполнили [дополнительное задание №3](https://github.com/digital-academy-devops/github-actions-module#%D0%B4%D0%BE%D0%BF%D0%BE%D0%BB%D0%BD%D0%B8%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE) в работе по [GitHub Actions](https://github.com/digital-academy-devops/github-actions-module), чтобы иметь возможность опубликовать собранный образ приложения на Dockerhub.

## Задание

1. В репозиторий с тестовым приложением, добавьте код развертывания в k8s в любом, удобном для Вас, варианте:
   - Статические манифесты;
   - Kustomize;
   - Helm chart.
1. Добавьте развертывание своего приложения в [ArgoCD](https://argocd.dacdevops.ru), запущенный в [общем кластере](https://github.com/digital-academy-devops/terraform-gitops/blob/main/states/common) через репозиторий [k8s-examples](https://github.com/digital-academy-devops/k8s-examples).
1. Приложение должно быть доступно по доменному имени в зоне `dacdevops.ru` по протоколу HTTP.

## Дополнительно
1. Опубликуйте приложение через HTTPS.

## Рекомендации
- Развертывание осуществляется подобно локальному, реализованному в работе по [docker-compose](https://github.com/digital-academy-devops/docker-compose-module) в варианте без балансировщика.
- Для локального тестирования развертывания, используйте [minikube](https://minikube.sigs.k8s.io/docs/).
- Конфигурационный файл для доступа к [общему кластеру](https://github.com/digital-academy-devops/terraform-gitops/blob/main/states/common) закреплён в сообщениях группового чата.
- Для доступа к интерфейсу [ArgoCD](https://argocd.dacdevops.ru), используйте учетную запись администратора:
  - Имя пользователя: *admin*
  - Пароль: определён в `Secret` в [общем кластере](https://github.com/digital-academy-devops/terraform-gitops/blob/main/states/common) - `argocd/argocd-initial-admin-secret`

# Примеры
- [Код развертывания при помощи Kustomize](https://github.com/digital-academy-devops/docker-example/tree/main/deployment/kustomize).
- [Развертывание в ArgoCD](https://github.com/digital-academy-devops/k8s-examples/blob/main/apps/cv-mostashkin.yaml).
- [Pull request для k8s-examples](https://github.com/digital-academy-devops/k8s-examples/pull/1)
- Ссылка для доступа к приложению: http://mostashkin.dacdevops.ru
- Реализация автоматического выпуска сертификата для HTTPS в развертывании [ArgoCD](https://argocd.dacdevops.ru) в [общем кластере](https://github.com/digital-academy-devops/terraform-gitops/blob/main/states/common):
  - [Certificate](https://github.com/digital-academy-devops/k8s-examples/blob/main/argocd/certificate.yaml)
  - [Ingress](https://github.com/digital-academy-devops/k8s-examples/blob/main/argocd/ingress.yaml#L19)
  
 
