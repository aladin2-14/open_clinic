<template>
    <div class="space-y-4 my-4">
        <div class="font-poppins font-bold text-base mx-3.5 text-sky-900">Infrastructures</div>
        <div class="title font-poppins">
            <div @click="totalinfra()">
                <div class="key">Total</div>
                <div class="value">{{ money(static.total_infrastructures) }}</div>
            </div>
            <div @click="infra(static.etat_counts?.infrastructures.Bon_etat.code)">
                <div class="key">En bon état</div>
                <div class="value">{{ money(static.etat_counts?.infrastructures.Bon_etat.quantite) }}</div>
            </div>
            <div @click="infra(static.etat_counts?.infrastructures.Etat_neuf.code)">
                <div class="key">Neuf</div>
                <div class="value">{{ money(static.etat_counts?.infrastructures.Etat_neuf.quantite) }}
                </div>
            </div>
            <div @click="infra(static.etat_counts?.infrastructures.Etat_satisfaisant.code)">
                <div class="key">Satisfaisant</div>
                <div class="value">{{ money(static.etat_counts?.infrastructures.Etat_satisfaisant.quantite) }}</div>
            </div>
            <div class="" @click="infra(static.etat_counts?.infrastructures.Etat_insatisfaisant.code)">
                <div class="key">Insatisfaisant</div>
                <div class="value">{{ money(static.etat_counts?.infrastructures.Etat_insatisfaisant.quantite) }}</div>
            </div>
            <div @click="infra(static.etat_counts?.infrastructures.Mauvais_etat.code)">
                <div class="key">En mauvais état</div>
                <div class="value">{{ money(static.etat_counts?.infrastructures.Mauvais_etat.quantite) }}</div>
            </div>
            <div @click="infra(static.etat_counts?.infrastructures.A_remplacer.code)">
                <div class="key">A remplacer</div>
                <div class="value">{{ money(static.etat_counts?.infrastructures.A_remplacer.quantite) }}</div>
            </div>
            <div>
                <div class="key">Fraction</div>
                <div class="value">{{ money((static.etat_counts?.infrastructures.Bon_etat.quantite /
                    static.total_infrastructures) * 100)}}%</div>
            </div>
        </div>
        <div class=" font-bold text-base mx-3.5 text-sky-900">Equipements</div>
        <div class="title font-poppins">
            <div @click="totalequi()">
                <div class="key">Total</div>
                <div class="value">{{
                    money(static.total_equipements) }}</div>
            </div>
            <div @click="infoEquistatus(static.status_counts?.equipements?.Fonctionnel_et_en_service?.code)">
                <div class="key">Fontionnel et en service</div>
                <div class="value">{{
                    money(static.status_counts?.equipements?.Fonctionnel_et_en_service?.quantite) }}</div>
            </div>
            <div @click="infoEquistatus(static.status_counts?.equipements?.Fonctionnel_et_hors_service?.code)">
                <div class="key">Fontionnel et hors service</div>
                <div class="value">{{
                    money(static.status_counts?.equipements?.Fonctionnel_et_hors_service?.quantite) }}</div>
            </div>
            <div @click="infoEquistatus(tatic.status_counts?.equipements?.Non_reparable?.code)">
                <div class="key">Non reparable</div>
                <div class="value">{{
                    money(static.status_counts?.equipements?.Non_reparable?.quantite) }}</div>
            </div>
            <div @click="infoEquistatus(static.status_counts?.equipements?.Maintenance_requise?.code)">
                <div class="key">Maintenance requise</div>
                <div class="value">{{
                    money(static.status_counts?.equipements?.Maintenance_requise?.quantite) }}</div>
            </div>
            <div @click="infoEqui(static.etat_counts?.equipements.Bon_etat.code)">
                <div class="key">En bon état</div>
                <div class="value">{{ money(static.etat_counts?.equipements.Bon_etat.quantite) }}</div>
            </div>
            <div @click="infoEqui(static.etat_counts?.equipements.Etat_neuf.code)">
                <div class="key">Etat neuf</div>
                <div class="value">{{ money(static.etat_counts?.equipements.Etat_neuf.quantite) }}
                </div>
            </div>
            <div @click="infoEqui(static.etat_counts?.equipements.Etat_satisfaisant.code)">
                <div class="key">Etat satisfaisant</div>
                <div class="value">{{ money(static.etat_counts?.equipements.Etat_satisfaisant.quantite) }}</div>
            </div>
            <div @click="infoEqui(static.etat_counts?.equipements.Etat_insatisfaisant.code)">
                <div class="key">Etat insatisfaisant</div>
                <div class="value">{{ money(static.etat_counts?.equipements.Etat_insatisfaisant.quantite) }}</div>
            </div>
            <div @click="infoEqui(static.etat_counts?.equipements.Mauvais_etat.code)">
                <div class="key">En mauvais état</div>
                <div class="value">{{
                    money(static.etat_counts?.equipements.Mauvais_etat.quantite) }}</div>
            </div>
            <div @click="infoEqui(static.etat_counts?.equipements.A_remplacer.code)">
                <div class="key">A remplacer</div>
                <div class="value">{{
                    money(static.etat_counts?.equipements.A_remplacer.quantite) }}</div>
            </div>
            <div>
                <div class="key">Fraction</div>
                <div class=" value">{{
                    money((static.etat_counts?.equipements.Bon_etat.quantite / static.total_equipements) * 100) }}%
                </div>
            </div>
        </div>
        <div class=" font-bold text-base mx-3.5 text-sky-900">Performance</div>
        <div class="title">
            <div>
                <div class="key">préventions</div>
                <div class="value">{{
                    money(static?.performance_counts?.interventions.Maintenance_preventive.quantite) }}</div>
            </div>
            <div>
                <div class="key">Programmées</div>
                <div class="value">{{
                    money(static?.performance_counts?.programmes) }}</div>
            </div>
            <div>
                <div class="key">couverts</div>
                <div class="value">{{
                    money(static?.performance_counts?.couverts) }}</div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from '../axios';
export default {
    data() {
        return {
            static: this.$store.state.static,
            start_date: '',
            end_date: '',
            lieu: this.$store.state.user.default_service_id
        }
    },
    methods: {
        infra(info) {
            this.$store.state.code = info
            this.$router.push('/Infrastructure')
        },
        infoEqui(eq) {
            this.$store.state.codeEqui = eq
            this.$router.push('/Inventaire')
        },
        infoEquistatus(status){
            this.$store.state.codeEquistatus = status
            this.$router.push('/Inventaire')
        },
        totalinfra(){
            this.$store.state.code = ''
            this.$router.push('/Infrastructure')
        },
        totalequi(){
            this.$store.state.codeEqui = ''
            this.$router.push('/Inventaire')
        },
    },
    watch: {
        "$store.state.static"(newVal) {
            this.static = newVal
        }
    },
    mounted() {
        if (this.$store.state.static.length === 0 ?? '') {
            this.$store.state.loader = true
            this.getStatics(this.start_date, this.end_date, this.lieu)
        } else {
            this.static = this.$store.state.static
        }
    }

}
</script>

<style></style>