<template>
  <div aria-hidden="true" class="modal fade delete" id="deleteModal" role="dialog">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <i class="icon icon-hapus"></i>
                    <span class="modal-title">Hapus Persediaan</span>
                </div>
                <div class="modal-body">
                    Apakah anda yakin akan menghapus<br>
                    <span v-if="selected.length > 1">{{ selected.length }} produk ini dari rak {{ nomorRak }}?</span>
                    <span v-if="selected.length == 1">produk {{ selected[0].nama_produk }} dari rak {{ nomorRak }}?</span>
                </div>
                <div class="modal-footer">
                    <button class="button" type="submit" @click="destroy">Hapus</button>
                    <span class="cancel" data-dismiss="modal">Batal</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import { mapState } from 'vuex'

    export default {
        methods: {
            destroy() {
                this.$store.dispatch('persediaan_store/destroy', {selected: this.selected, nomorRak: this.nomorRak, perPage: this.perPage})
            }
        },
        computed: {
            ...mapState('persediaan_store' ,{
                nomorRak: state => state.nomorRak,
                selected: state => state.selected,
                perPage: state => state.perPage,
            }),
        }
    }
</script>