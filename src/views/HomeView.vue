<script setup>
import SectionWrapper from '@/components/wrapper/SectionWrapper.vue'
import ComponentGrid from '@/components/wrapper/ComponentGrid.vue'
import DisplayCard from '@/components/wrapper/DisplayCard.vue'
import CustomButton from '@/components/CustomButton.vue'
import ScrollContainer from '@/components/ScrollContainer.vue'
import ImageSlider from '@/components/ImageSlider.vue'

const images = [
    'https://images.unsplash.com/photo-1640948612546-3b9e29c23e98?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxNDU4OXwwfDF8cmFuZG9tfHx8fHx8fHx8MTY0MzM5ODc5NQ&ixlib=rb-1.2.1&q=80&w=1600',
    'https://images.unsplash.com/photo-1641118961077-440391095cdc?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxNDU4OXwwfDF8cmFuZG9tfHx8fHx8fHx8MTY0MzM5ODc2Mw&ixlib=rb-1.2.1&q=80&w=1600',
    'https://images.unsplash.com/photo-1642190672487-22bde32965f7?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxNDU4OXwwfDF8cmFuZG9tfHx8fHx8fHx8MTY0MzM5ODcyOA&ixlib=rb-1.2.1&q=80&w=1600',
    'https://images.unsplash.com/photo-1641841344411-49dbd02896f4?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxNDU4OXwwfDF8cmFuZG9tfHx8fHx8fHx8MTY0MzM5ODcyOA&ixlib=rb-1.2.1&q=80&w=1600'
]
</script>

<template>
    <main>
        <SectionWrapper class="buttons">
            <template #SectionName>Buttons</template>
            <ComponentGrid>
                <DisplayCard>
                    <template #header> Custom Button </template>
                    <CustomButton variant="outline" size="md">
                        Button
                    </CustomButton>
                    <template #footer>
                        Inspired by shadcn-ui. uses 'variant' and 'size' custom
                        properties to choose between predefined button
                        layouts.</template
                    >
                </DisplayCard>
            </ComponentGrid>
        </SectionWrapper>
        <SectionWrapper class="display-elements">
            <template #SectionName>Display Elements</template>
            <ComponentGrid>
                <DisplayCard>
                    <template #header> Scroll Container </template>
                    <ScrollContainer />
                    <template #footer>
                        requires height or max-height to be set on the parent.
                        Scroll is limited to the container and can't "spill"
                        into surrounding elements
                    </template>
                </DisplayCard>
                <DisplayCard>
                    <template #header> Image Slider </template>
                    <ImageSlider :images="images" />
                    <template #footer>
                        Will Display Slider Controls only if there is more then
                        1 image in the provided images Array. Has Control Skip
                        Link, aria labels and focus-visible effects for all
                        Control elements.
                    </template>
                </DisplayCard>
            </ComponentGrid>
        </SectionWrapper>
    </main>
</template>
