<!--
// Copyright © 2020, 2021 Anticrm Platform Contributors.
//
// Licensed under the Eclipse Public License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License. You may
// obtain a copy of the License at https://www.eclipse.org/legal/epl-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
//
// See the License for the specific language governing permissions and
// limitations under the License.
-->
<script lang="ts">
  import type { Attachment } from '@hcengineering/attachment'
  import core, { TxCUD, TxCreateDoc, TxProcessor } from '@hcengineering/core'
  import AttachmentPresenter from '../AttachmentPresenter.svelte'
  import RemovedAttachmentPresenter from '../RemovedAttachmentPresenter.svelte'

  export let tx: TxCUD<Attachment>
  export let value: any

  const doc = tx._class === core.class.TxCreateDoc ? TxProcessor.createDoc2Doc(tx as TxCreateDoc<Attachment>) : value
</script>

{#if tx._class === core.class.TxRemoveDoc}
  <RemovedAttachmentPresenter value={doc} />
{:else}
  <AttachmentPresenter value={doc} />
{/if}
