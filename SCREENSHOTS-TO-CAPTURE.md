# Screenshots to capture — Plivo & Vobiz SIP integration docs

Internal capture checklist for the two BYO-SIP dialer guides:

- `general/dialer/plivoSipIntegration.mdx`
- `general/dialer/vobizSipIntegration.mdx`

Each `<Frame>` in those pages references a specific image. Capture the screen, name the file **exactly** as listed, and drop it into the matching folder. Filenames are case-sensitive and the extension must be `.jpeg`.

---

## General rules for every shot

- **Resolution:** capture at a consistent browser width (≈1440px) so all shots match.
- **Format:** save as `.jpeg` (the doc references use `.jpeg`, not `.png`).
- **Crop:** show the full relevant panel — don't crop so tight the menu/context is lost.
- **Sensitive data:** **redact or use test values.** Never screenshot a real credential password in clear text — mask it (e.g. `••••••••`). Use a **demo/test phone number** and a **test trunk**, not a live customer's.
- **Language/region:** keep the console in **English**; if your account defaults to another region, note it in the screenshot's surrounding text or pick a US number for consistency with the examples (`+1…`).
- **Highlighting:** a thin red box or arrow on the key field helps the reader — keep it subtle.

> After dropping files in, you can delete the `.gitkeep` in each folder (harmless to leave it).

---

## ✅ Capture checklist

### 🟠 `images/plivo/` — Plivo console (cx.plivo.com)

> **Status (2026-08-05):** ✅ Captured & wired up → `01-console-sip-trunking`, `03-create-outbound-trunk`, `04-termination-domain`, `06-create-inbound-trunk`, `08-primary-uri`. ⬜ Still needed → `02-buy-number`, `05-create-credentials`. 🗑 Stray on disk → `Screenshot 4.jpg` (Org settings → API keys / auth-token modal — not used by this guide; safe to delete).

- [ ] **`01-console-sip-trunking.jpeg`**
  - **Path:** Plivo console home → left sidebar
  - **Capture:** the sidebar with **SIP Trunking (Zentrunk)** item visible/highlighted.
  - **Highlight:** the **SIP Trunking** menu entry.

- [ ] **`02-buy-number.jpeg`**
  - **Path:** Phone Numbers → **Buy New Number**
  - **Capture:** the search form with **Capability = Voice** selected and a result list.
  - **Highlight:** the **Capability → Voice** filter.

- [ ] **`03-create-outbound-trunk.jpeg`**
  - **Path:** SIP Trunking → **Outbound Trunks** → **Create New Outbound Trunk**
  - **Capture:** the create form — trunk name filled (e.g. `qcall-outbound`) and **Trunk Authentication = Credentials List** selected.
  - **Highlight:** the **Credentials List** auth option.

- [ ] **`04-termination-domain.jpeg`**
  - **Path:** the Outbound Trunk detail page (after save)
  - **Capture:** the generated termination SIP domain, format `{trunk_id}.zt.plivo.com`.
  - **Highlight:** the **termination SIP domain** value (this maps to QCall's **SIP Termination URI**).

- [ ] **`05-create-credentials.jpeg`**
  - **Path:** Outbound Trunk → Trunk Authentication → **+ Add New Credentials List**
  - **Capture:** the credentials form — Auth Group name, **Username**, **Password** fields.
  - **Redact:** mask the password (`••••••••`). Show the password rules hint if visible (5–20 chars, ≥1 special char).

- [ ] **`06-create-inbound-trunk.jpeg`**
  - **Path:** SIP Trunking → **Inbound Trunks** → **Create New Inbound Trunk**
  - **Capture:** the create form with a name and the **Link Numbers** dropdown showing the test DID selected. Leave **Primary URI** empty in this shot (it's filled in shot `08`).
  - **Highlight:** **Link Numbers** with the DID chosen.

- [ ] **`08-primary-uri.jpeg`**
  - **Path:** the Inbound Trunk (edit) page
  - **Capture:** the **Primary URI** field filled with a LiveKit-style host + `;transport=tcp`, e.g. `myproj-x1y2.sip.livekit.cloud;transport=tcp`.
  - **Highlight:** the **Primary URI** value and the `;transport=tcp` suffix.

---

### 🟣 `images/vobiz/` — Vobiz console (console.vobiz.ai)

- [ ] **`01-console-dashboard.jpeg`**
  - **Path:** Vobiz console dashboard right after sign-in.
  - **Capture:** the main dashboard. Account Auth ID/Token may be visible — if so, **redact** them.

- [ ] **`02-buy-number.jpeg`**
  - **Path:** **DID / Phone Numbers** section
  - **Capture:** number search/purchase with a **Voice** number selected.
  - **Highlight:** the **Voice** capability / the purchased test DID in E.164.

- [ ] **`03-create-trunk.jpeg`**
  - **Path:** **Trunks** → **Create**
  - **Capture:** create form with a name (e.g. `qcall-trunk`) and, after save, the generated **SIP domain** `{trunk_id}.sip.vobiz.ai`.
  - **Highlight:** the auto-provisioned **SIP domain** (maps to QCall's **SIP Termination URI**).

- [ ] **`04-create-credentials.jpeg`**
  - **Path:** trunk → **Credentials** → **Create Credential**
  - **Capture:** the username + password fields.
  - **Redact:** mask the password (`••••••••••••`).

- [ ] **`05-attach-did.jpeg`**
  - **Path:** the DID number's settings
  - **Capture:** the **associate DID with trunk** action (dropdown/checkbox + the trunk selected).
  - **Highlight:** the selected trunk binding.

- [ ] **`06-inbound-origination.jpeg`**
  - **Path:** trunk (or DID) → **inbound routing** settings
  - **Capture:** the inbound **destination / origination URI** set to the Bolify LiveKit SIP host (e.g. `myproj-x1y2.sip.livekit.cloud`).
  - **Highlight:** the **origination / destination URI** field.

---

### 🔵 `images/qcall/` — Bolify dashboard (login.bolifyai.com) — **shared by both docs, capture once**

- [ ] **`add-sip-dialer.jpeg`**
  - **Path:** Bolify dashboard → **Settings → Dialers** → **➕ Add Dialer**
  - **Capture:** the dialer-type picker with **SIP** selected.
  - **Highlight:** the **SIP** option.

- [ ] **`sip-dialer-form.jpeg`**
  - **Path:** the Add SIP Dialer form
  - **Capture:** the form filled in — Dialer Name, Phone Number (test DID, E.164 with `+`), SIP Termination URI, SIP Username, SIP Password.
  - **Redact:** mask the **SIP Password** field. Use the carrier's test termination domain (e.g. `…​.zt.plivo.com` or `…​.sip.vobiz.ai`) — a generic shot works for both guides since the form is identical.

- [ ] **`sip-config-uri.jpeg`**
  - **Path:** the saved dialer's **SIP configuration** view
  - **Capture:** the resulting **LiveKit SIP URI** (`yourproject.sip.livekit.cloud`) that the user copies back to the carrier.
  - **Highlight:** the **LiveKit SIP URI** value.

---

## After capturing

1. Drop each `.jpeg` into its folder (`images/plivo/`, `images/vobiz/`, `images/qcall/`).
2. (Optional) remove the `.gitkeep` files once a real image is in each folder.
3. Preview locally with `mintlify dev` (from the `documentation/` repo) and skim both pages to confirm every `<Frame>` renders.
4. Commit the images together with the two `.mdx` changes and the `docs.json` registration.
