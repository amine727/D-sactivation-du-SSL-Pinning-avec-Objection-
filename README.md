# LAB 16 — Inspection HTTPS Android : Désactivation du SSL Pinning avec Objection + Burp Suite

## Objectif du Lab

Ce lab a pour objectif de :

- Installer Frida et Objection.
- Configurer un émulateur Android pour l’analyse dynamique.
- Désactiver le SSL Pinning d’une application Android.
- Intercepter le trafic HTTPS avec Burp Suite.
- Vérifier les requêtes HTTPS de l’application `InsecureBankv2`.

---

# Environnement du Lab

| Outil | Version |
|---|---|
| Windows 11 | OS principal |
| Android Emulator | Android 9 |
| Frida | 17.9.1 |
| Objection | 1.12.4 |
| Burp Suite | Community Edition |

---

# Vérification des outils

Les commandes suivantes permettent de vérifier :
- la détection de l’émulateur Android,
- la version de Frida,
- la version d’Objection.

```bash
adb devices
frida --version
objection version
```

## Résultat

<img width="921" height="231" alt="25" src="https://github.com/user-attachments/assets/e8fcc7cb-eae1-437e-802f-e468ea314625" />

---

# Désactivation du SSL Pinning

L’application utilisée est :

```text
com.android.insecurebankv2
```

La commande suivante permet de lancer Objection et désactiver automatiquement le SSL Pinning :

```bash
objection -g com.android.insecurebankv2 explore --startup-command "android sslpinning disable"
```

---

# Résultat de l’injection Objection

Les hooks SSL ont été injectés avec succès :

- `Custom TrustManager ready`
- `verifyChain() overridden`
- `checkTrustedRecursive() overridden`

Cela confirme que le SSL Pinning a été désactivé.

## Capture


---<img width="1677" height="470" alt="26" src="https://github.com/user-attachments/assets/d371a02a-448a-4693-aaf2-f68c2a0fccec" />




# Validation

Après la désactivation du SSL Pinning :

- l’application ne bloque plus les certificats Burp,
- les requêtes HTTPS peuvent être interceptées,
- le trafic peut être analysé dans Burp Suite.

---

# Résultat Final

Le laboratoire a permis de :

✅ Configurer Frida et Objection  
✅ Connecter l’émulateur Android  
✅ Désactiver le SSL Pinning  
✅ Préparer l’interception HTTPS avec Burp Suite  
✅ Réaliser une analyse dynamique de l’application Android  

---
