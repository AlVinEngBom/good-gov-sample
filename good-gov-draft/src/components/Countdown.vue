<template>
    <div v-if="loaded" class="fs-5">
        <section style="display: flex; justify-content: center;">
            <h6 v-if="!expired">Days Until Deployment</h6>
            <h5 v-else>Timer Is Done</h5>
        </section>
        <section style="display: flex; justify-content: center;">
            <div class="badge bg-primary text-wrap p-2" style="width: 6rem;">
                {{displayDays}}
                <div>days</div>
            </div>
            <span class="p-1"></span>
            <div class="badge bg-primary text-wrap p-2" style="width: 6rem;">
                {{displayHours}}
                <div>hours</div>
            </div>
            <span class="p-1"></span>
            <div class="badge bg-primary text-wrap p-2" style="width: 6rem;">
                {{displayMinutes}}
                <div>minutes</div>
            </div>
            <span class="p-1"></span>
            <div class="badge bg-primary text-wrap p-2" style="width: 6rem;">
                <div>{{displaySeconds}}</div>
                <div>seconds</div>
            </div>
        </section>
    </div>
</template>

<script>
export default {
    name: 'Countdown',
    props: ["year", "month", "date", "hour", "minute", "second", "millisecond"],
    data: () => ({
        displayDays: 0,
        displayHours: 0,
        displayMinutes: 0,
        displaySeconds: 0,
        loaded: false,
        expired: false
    }),
    computed: {
        _seconds: () => 1000,
        _minutes() {
            return this._seconds * 60;
        },
        _hours() {
            return this._minutes * 60;
        },
        _days() {
            return this._hours*24
        },
        end() {
            return new Date(
                this.year,
                this.month,
                this.date,
                this.hour,
                this.minute,
                this.second,
                this.millisecond
            );
        }
    },
    mounted() {
        this.showRemaining();
    },
    methods: {
        formatNum: num => (num < 10 ? "0" + num : num),

        showRemaining() {
            const timer = setInterval(() => {
                const now = new Date();
                // const end = new Date(2021, 4, 22, 10, 10, 10, 10);
                const distance = this.end.getTime() - now.getTime();

                if (distance < 0) {
                    clearInterval(timer);
                    this.expired = true;
                    this.loaded = true;
                    return;
                }

                const days = Math.floor(distance/this._days);
                const hours = Math.floor((distance % this._days) / this._hours);
                const minutes = Math.floor((distance % this._hours) / this._minutes);
                const seconds = Math.floor((distance % this._minutes) / this._seconds);
                this.displayMinutes = this.formatNum(minutes);
                this.displaySeconds = this.formatNum(seconds);
                this.displayHours = this.formatNum(hours);
                this.displayDays = this.formatNum(days);
                this.loaded = true;
            }, 1000);
        }
    }
}
</script>
